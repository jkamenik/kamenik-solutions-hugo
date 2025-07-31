---
title: 'Docker Details - Dumb Init'
date: 2017-10-21
lastmod: 2017-10-21

# Keywords help in classifying content
keywords:
  - Docker Details Dumb Init
  - Docker
  - Dumb Init
---

If you don't control the "init" process of docker then you are doing it wrong. But don't worry there is an easy fix. Before I explain the solution, I should explain the issue. Almost every process you run in Linux will likely run at least 1 child process. And Linux expects that every parent will properly care for its children by propagating kernel signals like SIGTERM, and by cleaning up child zombie processes. If all else fails the Linux `init` process will do that on behalf of Linux and all is happy.

However, programmers generally don't know the requirements of dealing with child processes, and linux clean up after itself so unless you already know what to do testing won't show issues. The issue comes because Docker doesn't provide an `init` process for the container, so your child processes will not get signals, zombies will be created, and eventually things will terminate uncleanly or hang indefinately.

<!--more-->

## Solution: Use dumb-init

[dumb-init](https://github.com/Yelp/dumb-init) provides a very small `init` runtime that deals with signals and zombie processes. And nothing else! It is a tiny 45Kb statically compiled and will work inside any docker container as the entrypoint.

`dumb-init` has the ability to do signal-rewriting which is very important if you are using `apache` which uses SIGWINCH for a graceful shutdown or `nginx` which uses SIGQUIT. Many other programs also use different signals then TERM to mean graceful shutdown.

Another nice benefit of `dumb-init` is that it will terminate the container immediately on any of the termination signals, even if the child processes ignore the signals. This prevents stall-out of container termination in {{% wl Kubernetes %}}, {{% wl "Docker Swarm" %}}, and {{% wl "Docker Compose" %}}.

### Test your containers

To test your containers send it the SIGHUP, SIGINT, SIGTERM, SIGUSR1, and SIGUSR2 signals to your running container. All of them should immediately start the shutdown process.

Lets assume you have a container like the following container

```docker
FROM alpine:3.5

COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
RUN apk add --no-cache bash

ENTRYPOINT ["/entrypoint.sh"]
```

The `entrypoint.sh` looks like this. It will print the signal it gets but only exit cleanly if it gets USR1. I also added a 2s wait on USR1 to simulate a graceful shutdown. All the signal handlers should be called in turn until one exists the program.

```bash
#!/bin/bash

trap "echo TERM" TERM
trap "echo HUP" HUP
trap "echo INT" INT
trap "echo QUIT" QUIT
trap "echo USR1; sleep 2; exit 0" USR1
trap "echo USR2" USR2

ps aux
tail -f /dev/null
```

You can build the container with a command like `docker build -t my_container`. If you run it with `docker run --rm -ti --name my_container my_container` you will get the following output:

```
PID   USER     TIME   COMMAND
    1 root       0:00 {entrypoint.sh} /bin/bash /entrypoint.sh
    7 root       0:00 ps aux
```

You can send any signal you want to the container via `docker kill -s HUP my_container` (replace HUP with various signals). None of the signals are printed! To double check run `docker stop`, which will sent TERM, then wait 10 seconds before sending KILL.

```
$ time docker stop my_container
my_container

real	0m10.761s
user	0m0.011s
sys	0m0.015s
```

So here we can tell that stop waited the full 10s and still needed to send KILL.

### Fixing the issue

Changing nothing about `/entrypoint.sh` we can fix this by updating the Dockerfile as follows.

```docker
FROM alpine:3.5

COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
RUN apk add --no-cache bash

# Change 1: Download dumb-init
ADD <https://github.com/Yelp/dumb-init/releases/download/v1.2.0/dumb-init_1.2.0_amd64> /usr/local/bin/dumb-init
RUN chmod +x /usr/local/bin/dumb-init

# Change 2: Make it the entrypoint.  The arguments are optional
ENTRYPOINT ["/usr/local/bin/dumb-init","--rewrite","15:10","--"]
CMD ["/entrypoint.sh"]

```

Again start the container and run `docker stop`

```
$ time docker stop my_container
my_container

real	0m2.778s
user	0m0.011s
sys	0m0.013s
```

Here you can see it exists immediately after the simulated graceful shutdown meaning it got and processed the USR1 signal, even though it was sent the TERM signal. The output of the container is

```
PID   USER     TIME   COMMAND
    1 root       0:00 /usr/local/bin/dumb-init --rewrite 15:10 -- /entrypoint.s
    7 root       0:00 {entrypoint.sh} /bin/bash /entrypoint.sh
    8 root       0:00 ps aux
User defined signal 1
USR1
0
```

In case you want to double check that TERM was actually used we can use `docker kill -s TERM` to explicitly send the TERM signal:

```
$ docker kill -s TERM my_container
my_container

PID   USER     TIME   COMMAND
    1 root       0:00 /usr/local/bin/dumb-init --rewrite 15:10 -- /entrypoint.s
    7 root       0:00 {entrypoint.sh} /bin/bash /entrypoint.sh
    8 root       0:00 ps aux
User defined signal 1
USR1
0
```

We still get USR1 as the signal.

## Honorable Mentions

The following are worth mentioning, though I don't use them.

### tini

[tini](https://github.com/krallin/tini) is an alternative to `dumb-init`. It is a few months older then `dumb-init` but doesn't provide the signal rewriting that you are going to need for many of the programs you will want to run.

It is also 850Kb for the statically compiled version (vs 45kb for `dumb-init`). Not a huge number, but given it has fewer features it isn't worth the bloat.

Also, if you do use `tini` remember to use the `-g` options so that all child processes are signaled, like would be done from `init` during a shutdown. This is the default for `dumb-init` but needs to be enabled for `tini`.

### docker run --init

The `--init` flag was added to docker 1.13 to run `tini` as the init process before the ENTRYPOINT is executed. Its a cute addition, but isn't used by Kubernetes, Docker Swarm, or Docker Compose. This might be fixed in the future, but for now it is best to ignore this option.
