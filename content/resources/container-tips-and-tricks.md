---
title: 'Container Tips and Tricks'
date: 2025-04-18
lastmod: 2025-04-18

weight: 2

# Keywords help in classifying content
keywords:
  - Container Tips and Tricks
  - Containers
  - Tips and Tricks
  - How Tos
  - Docker
---

<!--more-->

The following are useful tricks for containers.

## Tools Containers

It is often useful to put tools like `gcloud`, `aws`, and others in containers and use the containers in place of installing programs directly on the computer.  This makes the commands more portable, but also make it easier to upgrade and rebuild should something go wrong.

First, install [docker-desktop](https://www.docker.com/products/docker-desktop/) for your give OS, or some other container runtime.

Second, create a script like the following and put it somewhere it can be loaded.

```bash
#!/bin/bash

APP_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")/.." && pwd)"
source "$APP_DIR/lib/log.sh"

# docker_run does some basic stuff to to setup a
# `docker run <standard args>` so that the rest of the args
# can be blindly passed in.
function docker_run() {
  local args=("--rm") # Make a local array of args

  # If standard out/in is a terminal
  if [[ -t 0 ]]; then
    args["${#args[@]}"]="--interactive"
    args["${#args[@]}"]="--tty"
  else
    info "No input"
  fi

  debug "Args:" "${args[@]}"

  # Note: if you use a different docker runtime (like podman)
  # then simply switch the args and the command here.
  docker run "${args[@]}" "$@"
}
```

Third, create a wrapper for the function you want.  For example, the AWS CLI.

```bash
#!/bin/bash

# Trick from the bash tips and tricks page
APP_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")/.." && pwd)"

# Load the docker script from above
source "$APP_DIR/lib/docker.sh"

# this is the container name you will be building
IMAGE_TAG="aws-cli"

# Setup the local directories that get mounted
# That way the auth state gets persisted between
# runs of the container
SRC_PATH=/workdir

mkdir -p "$HOME/.aws"
mkdir -p "$HOME/.kube"

MOUNT_PATHS=(
-v "$APP_DIR:$SRC_PATH"
-v "$HOME/.kube:/root/.kube"
-v "$HOME/.aws:/root/.aws"
)

# Now pass it all to docker_run
docker_run "${MOUNT_PATHS[@]}" --workdir "$SRC_PATH" --entrypoint="/usr/local/bin/aws" "$IMAGE_TAG" "$@"
```

Finally, build / cache the needed CLI tool as a local container.

```Dockerfile
# Often there exists a public container with the tool
FROM amazon/aws-cli:latest

# Often a good idea to label so you know you built it, and when
LABEL Maintainer="Myself"
LABEL Revision="20211008150705"

# Now install any other tools that tools that might help when using
# this container.
#
# kubectl allows for the connection to AWS EKS clusters
# JQ is a JSON CLI parser to help with AWS API output.
# YQ is the same as JQ but for YAML, so works nicer with
#  K8s objects.
ENV KUBECTL_VERSION=1.19.6
ENV JQ_VERSION=jq-1.6
ENV YQ_VERSION=v4.7.1

# hadolint ignore=DL3020
ADD "https://amazon-eks.s3.us-west-2.amazonaws.com/${KUBECTL_VERSION}/2021-01-05/bin/linux/amd64/kubectl" /usr/local/bin/kubectl
# hadolint ignore=DL3020
ADD "https://github.com/stedolan/jq/releases/download/${JQ_VERSION}/jq-linux64" /usr/local/bin/jq
# hadolint ignore=DL3020
ADD "https://github.com/mikefarah/yq/releases/download/${YQ_VERSION}/yq_linux_amd64" /usr/bin/yq

RUN chmod +x /usr/local/bin/*
RUN yum install -y tar-1.* && yum clean all

ENTRYPOINT ["/bin/bash"]
```

For bonus points you can setup a nightly CI pipeline to build containers like this and push to public or private image repo.  But I leave that as an exercise for the audience.
