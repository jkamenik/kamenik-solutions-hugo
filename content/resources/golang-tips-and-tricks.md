---
title: 'Golang Tips and Tricks'
date: 2025-04-18
lastmod: 2025-04-18

weight: 4

# Keywords help in classifying content
keywords:
  - Golang Tips and Tricks
  - GoLang
  - Go
  - Tips and Tricks
  - How Tos
---

<!--more-->

The following are some basics on GoLang.

## How to

- [justforfunc: Programming in Go - YouTube](https://www.youtube.com/channel/UC_BzFbxG2za3bp5NRRRXJSw)
- [GitHub - campoy/justforfunc: The repository for the YouTube series JustForFunc](https://github.com/campoy/justforfunc)
- [GitHub - campoy/go-tooling-workshop: A workshop covering all the tools gophers use in their day to day life](https://github.com/campoy/go-tooling-workshop)
- [Documentation - The Go Programming Language](https://golang.org/doc/)
- [pkg.go.dev](https://pkg.go.dev/) - Documentation on most go packages
- [Go Docker image](https://hub.docker.com/_/golang)
- [golang-standards · GitHub](https://github.com/golang-standards) - Shows an example project layout and project-templatez

## Quick start

1. Install Go: `brew install go`
2. You may want to use docker which is what build systems will use

    ```bash
    docker pull golang:1.15.4
    docker run -rm -v "$PWD":/code -w "/code" golang:1.15.4 go build -v
    ```

3. Install Go plugin to your favorite Editor (e.g., go-plus for Atom)
4. Setup your repo
5. If a library then it should be in `$GOPATH/src/<url path>`

### General project layout

[GitHub - golang-standards/project-layout: Standard Go Project Layout](https://github.com/golang-standards/project-layout)

Universal files:

1. `README.md` - Every project should have one
2. `LICENSE.md` - Every project should have one
3. `run` - A script to easily build or test the code
4. `go.mod` - initialize as a module `go mod init <name>`
5. `go.sum` - commit this if it exists.

#### `/cmd/<name>`

This is the place for the `main` package.  It should build into an executable.  `<name>` should be the name of the command you want to build.  You will build it via `go build cmd/<name>`.

Not much code should be here.  Just a means to load stuff from `/internal`, or `/pkg`.

#### `/internal`

Private code should be here.  This is enforced by the compiler

#### `/pkg`

Library code that is ok for others to use.

#### `/vendor` (managed)

This directory is (or should be) managed by your dependency manager and not by you directly.

#### `/build`

Not universally recommended, but if your build system takes scripts then it should be `/build/ci` and then linked to whatever location the build system wants it to actually be.  Where possible it is just a thing wrapper around `run`.

## Tools

1. `go` - The general tool for go
2. `devel` - Go debugger
3. [GitHub - tsliwowicz/go-wrk: go-wrk - a HTTP benchmarking tool based in spirit on the excellent wrk tool](https://github.com/tsliwowicz/go-wrk)
4. [goimports](https://pkg.go.dev/golang.org/x/tools/cmd/goimports) - An improved `fmt` tool that also handls imports

## Libraries

- https://awesome-go.com/ - A curated list of awesome Go libraries
- https://threedots.tech/post/list-of-recommended-libraries/ - 22 libraries known to work in production

### Command Tools

[GitHub - spf13/cobra: A Commander for modern Go CLI interactions](https://github.com/spf13/cobra)

### Configuration Loading

- [GitHub - spf13/viper: Go configuration with fangs](https://github.com/spf13/viper)

### Database

Examples:

1. [concourse/atc/db](https://github.com/concourse/concourse/tree/master/atc/db) - Does not use an ORM or Migration library, example of how to do it manually

#### DB Drivers

- [https://golang.org/pkg/database/sql/](https://golang.org/pkg/database/sql/) - Golang's built in SQL Library, most have a compatable interface
- [https://github.com/lib/pq](https://github.com/lib/pq) - `database/sql` Postgres Driver
- [https://github.com/jackc/pgx](https://github.com/jackc/pgx) - Postgres specific driver as well as `database/sql` compatible driver.  The specific driver interface is more performant, but the standard interface is available for use with other libraries.
- [https://github.com/Masterminds/squirrel](https://github.com/Masterminds/squirrel) - Fluent SQL generation for golang makes queries easier.

#### DB ORMs

1. [https://gorm.io](https://gorm.io) - A Rails-type ORM similar to ActiveRecord.
2. [https://github.com/go-pg/pg](https://github.com/go-pg/pg) - Golang ORM with focus on PostgreSQL features and performance
3. [https://godoc.org/github.com/Masterminds/structable](https://godoc.org/github.com/Masterminds/structable) - Simple Struct to DB mapper / recorder

#### DB Migrations

1. [https://github.com/golang-migrate/migrate](https://github.com/golang-migrate/migrate) - Database migrations. CLI and Golang library.  This is library agnostic.
    1. It has a [BinData](https://github.com/golang-migrate/migrate/blob/master/source/go_bindata) source driver that allows SQL migration files to be loaded directly into binary.
2. [https://gorm.io](https://gorm.io) - A Rails-type ORM similar to ActiveRecord, with a similar migration style
    1. WARNING: in practice these style migration are fragile as there is a tight coupling to the record.

### Git

https://pkg.go.dev/github.com/go-git/go-git/v5 - A pure Golang implementation of Git

#### Gerrit

> [!NOTE]
> As a Google maintained project all Golang code is maintained in public version of their GitOnBorg system which uses Gerrit as the review system.  To contribute to the main golang code base you have to understand Gerrit.

Gerrit is the code review system used by Google's Public GoLang team.

Changes (cls) are created by pushing to a special branch called `refs/for/<target branch>`.  This opens the Equivalent of a GitHub PR.  With the difference being that in Gerrit a commit is the unit of work, and in GitHub the branch is.

Topics are a way of associating changes across multiple repos.  It is interfaced by using the config `push.pushOption = topic=<name>`, or doing it via an option during the push: `git push ... -o topic=<name>`, or `git push origin HEAD:refs/for/main%topic=<name>`.

https://github.com/andygrunwald/go-gerrit - Gerrit API client

### Graphs

1. [https://github.com/dominikbraun/graph](https://github.com/dominikbraun/graph) - Generic graph data-structure

### HTTP

1. [http - The Go Programming Language](https://golang.org/pkg/net/http/)

2. [GitHub - justinas/alice: Painless middleware chaining for Go](https://github.com/justinas/alice) - Allows Middlewares

3. [GitHub - throttled/throttled: Package throttled implements rate limiting access to resources such as HTTP endpoints.](https://github.com/throttled/throttled)

4. [GitHub - justinas/nosurf: CSRF protection middleware for Go.](https://github.com/justinas/nosurf)

#### HTTP Router / MUX

1. [GitHub - vmihailenco/treemux: Fast and flexible HTTP router](https://github.com/vmihailenco/treemux)

### Logging

1. [log](https://pkg.go.dev/log) - The logging package is enough if all you want to do is add a date

#### Structured Logging

In most cases structured logging is what you want.

1. [slog](https://pkg.go.dev/log/slog) - slog augments log by adding levels, and fields.  It is usually enough.

1. [GitHub - sirupsen/logrus: Structured, pluggable logging for Go.](https://github.com/sirupsen/logrus) - Dead project as of 2020-11

1. [GitHub - rs/zerolog: Zero Allocation JSON Logger](https://github.com/rs/zerolog)

1. [GitHub - uber-go/zap: Blazing fast, structured, leveled logging in Go.](https://github.com/uber-go/zap)

1. [GitHub - apex/log: Structured logging package for Go.](https://github.com/apex/log)

### Merging Objects

[GitHub - imdario/mergo: Mergo: merging Go structs and maps since 2013.](https://github.com/imdario/mergo)

#### Metrics (prometheus)

[prometheus · pkg.go.dev](https://pkg.go.dev/github.com/prometheus/client_golang/prometheus)

---

### Parsing

#### YAML

1. [https://gopkg.in/yaml.v2](https://gopkg.in/yaml.v2-) - Built-in yaml.v2
2. [sigs.k8s.io/yaml](http://sigs.k8s.io/yaml) - YAML parser from K8s / Helm
    1. Use this one when YAML and JSON inter-opt is needed.

```go
// Reading unstructured yaml
data := map[string]interface{}{}

bytes, err := yaml.Parse(fileBytes,&data)
if err != nil {
  return nil, err
}
```

### Static Files

[GitHub - markbates/pkger: Embed static files in Go binaries (replacement for gobuffalo/packr)](https://github.com/markbates/pkger)

### Testing

#### BDD

- https://github.com/onsi/ginkgo - BDD library
- https://github.com/onsi/gomega - Ginkgo’s Preferred Matcher Library

#### TDD

https://github.com/smartystreets/goconvey - A nicer testing framework, more TDD like
