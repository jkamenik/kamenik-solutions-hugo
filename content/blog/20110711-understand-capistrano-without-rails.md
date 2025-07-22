---
title: 'Understand Capistrano Without Rails'
date: 2011-07-11
lastmod: 2011-07-11

# Keywords help in classifying content
keywords:
  - Understand Capistrano Without Rails
  - Capistrano
  - Ruby on Railsß
---

I am working on a rails project and that rails project is distributed over several nodes in a cluster. However, each of those nodes is a standalone unit and the rails app is a small administrative frontend for that box only. For this reason the standard Capistrano deployment tasks will not work.  So some hacking is in order.

<!--more-->

Looking around I noticed a number of projects that were just deployment steps for other frameworks and stacks, but still required Capistrano. This got me thinking that maybe Capistrano is more then just a set of deployment steps. The wiki does not make this clear but there are three parts to Capistrano:

1. an engine to replicate (transactional) commands on any number of servers
2. a rake like DSL for defining tasks to perform on remote servers, and
3. a set of deployment recipes specifically tied to rails.

The first two items are what I need and by **not** including the default recipes I can do anything I want. Below is my understanding of how Capistrano works.

## Sample `config/deploy.rb` file

The below code is an example that will be reference throughout.

```ruby
role :servers, 'host1'

role :client, 'host2', 'host3'
role :client, 'host4', :special => true

task :install, :roles => :servers do
	run "uname -a"
end

task :test, :roles => :client do
	sudo 'echo TEST'
end

test :special, :roles => :client, :only => {:special => true} do
	sudo "echo SPECIAL"
end

```

## Understanding Roles

Capistrano uses "roles" to list servers with similar behaviors. The default recipe uses roles like "web" and "db" and makes it seem like that they are in some way special. They really are not. The only way they are used is by the "roles" option when defining a task.

When a task defines "roles" then it will only be called on the server that have that role (see sample). Additionally options can be added to the end of roles that act like flags that can later be used by tasks to filter. Armed with understanding we can easily create arbitrary roles for use in our deployment steps.

## Understanding Tasks

Capistrano is a simplified rake like syntax. If you are familiar with rake there are few gotcha:

1. tasks cannot take input, and
2. tasks and namespaces cannot overlap.

Both of these can be worked around however. Deployment tasks should never (NEVER) take user input. User input is a variable that cannot be repeated automatically. So armed with the knowledge that if you "need" user input in deployment then you are doing something wrong rework the system to not require user input and move on.

There is only one special task name that I have found ":default". If you make a task ":default" then it will simply become the task that is run when the namespace is called. It also, takes itself out of the help list so there is no task `<namespace>:default`.

### Understand Flags

Task provide the options "except" and "only" that work on role flags. In the sample there is a task `:special` that will only run for hosts with the "client" role that also have the `:special` flag set to true. The included deployment recipe adds `:primary` to the `:db` role to indicate that it is the only server on which migrations should be run. I currently have no use for flags, but it is nice to understand their behavior.

### Calling other tasks

In rake it is possible to say that a task depends on other tasks. In Capistrano it is not. This is not a problem since task is a wrapper around a method definition. Basically you can call a task in the current namespace by using its name like a method. And you can call methods in higher namespaces using "top".

```ruby
task :upload do
  puts "real upload"
end

namespace :child do
  task :upload do
    puts "child upload"
  end

  task :upload1 do
    top.upload
  end
end
```

```bash
$ cap upload
real upload

$ cap child:upload
child upload

$ cap child:upload1
real upload
```

## Understanding Connections

In addition to being a DSL to define deployment tasks Capistrano is also an SSH connection manager. Using the "run" or "sudo" function Capistrano will execute that string at a shell on each remote machine in turn. The gotcha is that each call to "run" or "sudo" opens an entirely new connection. Therefore if several things need to be done at once use `;` or `&&` to chain commands in a single shell.

```ruby
task :test do
  run "export TEST=foo && echo $TEST"
  run "echo $TEST"
end
```

```bash
$ with servers !test
** [out :: host1] foo
** [out :: host1]

$ with client !test
** [out :: host2] foo
** [out :: host3] foo
** [out :: host4] foo
** [out :: host2]
** [out :: host3]
** [out :: host4]
```

In the above example the ENV variable "TEST" is set to foo, but since the second "run" gets a new shell the ENV is reset. Also, in the second example it is clear that each "run" is executed on every server before it moves onto the next server.
