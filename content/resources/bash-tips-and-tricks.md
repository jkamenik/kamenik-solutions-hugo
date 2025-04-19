---
title: 'Bash Tips and Tricks'
date: 2025-04-18
lastmod: 2025-04-18

weight: 1

# Keywords help in classifying content
keywords:
  - Bash Tips and Tricks
  - Bash
  - Tips and Tricks
  - How Tos
---

<!--more-->

The following are common useful tricks for Bash programming.

## Directory Containing the Script

Many times it can be useful to get the directory of where the script lives even if `PWD` is set to something else.

```bash
APP_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )/." && pwd )"

source "$APP_DIR/../lib/mylib.sh"
```

## Iterate over lines in a file

> [!warning]
> The file will need an empty line at the end or you will miss the last line.

```bash
while IFS= read -r line; do
  echo "$line"
done < file
```

## Iterate over command output

Very similar to files command output can be treated like a file using the `<()` operator. This for example can be used to grep certain strings out, and or manipulate the line ahead of iterating.

```bash
while IFS= read -r line; do
  echo "$line"
done < <(ls .)
```

## Local OR and AND

With the `test` (`[`) command

```bash
if [ "$a" == 1 -a "$b" == 1 ]; then
  echo "a AND b"
fi

if [ "$a" == 1 -o "$b" == 1 ]; then
	echo "a OR b"
fi
```

With the build-in `[[`

```bash
if [[ "$a" == 1 && "$b" == 1 ]]; then
  echo "a AND b"
fi

if [[ "$a" == 1 || "$b" == 1 ]]; then
	echo "a OR b"
fi
```

## Logging

Very often logging is useful, especially in bash.  However, many times logging clobbers proper output.  The best solution is to use standard error for logging.  Also, it is usually useful to have levels of logging, so you put logging lines in your code that are unused by default.

```bash
function now() {
  TZ="UTC" date +"%Y%m%d%H%M%S"
}

function log() {
  echo "$@" >&2
}

function debug() {
  if [[ -n "$DEBUG" ]]; then
    log "$(now) DEBUG:" "$@"
  fi
}

function info() {
  log "$(now) INFO:" "$@"
}

function warn() {
  log "$(now) WARN:" "$@"
}

function error() {
  log "$(now) ERR:" "$@"
}

function fatal() {
  log "$(now) FATAL:" "$@"
  exit 1
}

## Usage
debug "This is a debug"
info "this is an info message"
```

# References

- [Bash-hackers wiki](http://wiki.bash-hackers.org/) *(bash-hackers.org)*
- [Shell vars](http://wiki.bash-hackers.org/syntax/shellvars) *(bash-hackers.org)*
- [Bash Guide](http://mywiki.wooledge.org/BashGuide) *(mywiki.wooledge.org)*
