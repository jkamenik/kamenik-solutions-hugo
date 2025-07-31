---
title: 'Managing Base Docker Images'
date: 2016-12-03
lastmod: 2016-12-03

# Keywords help in classifying content
keywords:
  - Managing Base Docker Images
  - Docker
---

Docker is a great way to package your code such that you can be sure it will run on any machine that has docker installed. However, maintaining your docker containers and publishing them to docker hub can be a bit of a challenge. The following are two ways I do it.

<!--more-->

## Option 1: Let docker hub do it

If your needs are simple then you can have Docker Hub monitor a repo and rebuild the docker file when you push a changed to the directory.

Docker hub maps branches to tags with "master" being the "latest" tag. If you want more docker tags (maybe multiple versions) then you will need to create multiple branches and reconfigure Docker Hub.

## Option 2: One repo to rule them all

The option that I generally go for is a single repo to manage all my docker containers. Where the directories map to the docker repos and to the tags. I do this because you "should" be separating your packaging from your source, and I like to keep similar things organized.

With this method you do not need to create the Docker Hub repos. They will be created by `docker push` from the `build.sh`, but you will need to manually edit the repo information on Docker Hub to make the repo useful for others.

If you wanted to automate it then you will need a CI service which allows docker images and [Docker-next-to-docker](http://jpetazzo.github.io/2015/09/03/do-not-use-docker-in-docker-for-ci/#the-solution). Setting up automation is beyond the scope of this entry.

The [docker-image repo](https://github.com/jkamenik/docker-images) directory would look a bit like this:

```
- /
  - jkamenik/
    - hugo/
      - 0.15/
        - Dockerfile
        - entrypoint.sh
      - latest -> ./0.15
      - README.md
  - my-private-repo.com/
    - emacs
      - 25.1
        - Dockerfile
  - build.sh
```

The highest level directory ("jkamenik") is the Docker hub account name. Or it could be a private docker repo. `build.sh` has not been tested against private repos, but it should work.

The 2nd level directory ("hugo") is the docker image name: "jkamenik/hugo". Within this directory is also where I put the `README.md`. This is because a Docker Hub Repo's information is independent of a tag; so it makes sense for me to manage it in the same way. After the first creation, or an update to the README, I copy and paste this information into the Docker Hub repo's information.

The 3rd level directory ("0.15") is the docker tag: "jkamenik/hugo:0.15". Also, the 3rd level directory can be a symlink, which is useful when tagging "latest" to a specific version.

The 4th level is where the `Dockerfile` and any supporting files go. A common pattern for me is to provide a script which will be the entry point. The behavior of this script is generally to check the argument list and if they look like program arguments blindly pass them to the default program. If they don't look like program arguments then execute them as the entry point.

```bash
# execute hugo without args
$ docker run jkamenik/hugo

# execute hugo with "-D"
$ docker run jkamenik/hugo -D

# execute bash
$ docker run jkamenik/hugo /bin/bash
```

The `build.sh` file takes 0 or 1 argument. If there are 0 arguments then it will build all directories. If there is 1 argument traverse that path and build only images there. For example:

```bash
# build all
$ ./build.sh

# build all private repos
$ ./build.sh my-private-repo.com

# build only the 0.15 verion of hugo
$ ./build.sh jkamenik/hugo/0.15
```

To see this all in action see [https://github.com/jkamenik/docker-images](https://github.com/jkamenik/docker-images)
