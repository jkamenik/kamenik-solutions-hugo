---
title: 'Go'
date: 2024-04-09
lastmod: 2025-05-08

# Keywords help in classifying content
keywords:
  - Go
  - GoLang

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: adopt

    # tools, techniques, platforms, languages & frameworks
    quadrant: languages

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

[Go](https://go.dev) is a language that google created to handle its unique scaling needs.  It turns out that designing for those needs, eliminates the performance and scale cliff that almost everyone experiences.  Since the language itself is fairly simple this has made it a boon for anywhere large scale and/or highly concurrent programming is needed.  For this reason it has become the de facto language for many DevOps tools, so if you are in that space then you should know it.

<!--more-->

> [!NOTE] GoLang
> Because "Go" is very generic "GoLang" can be used in search.

One of its core strengths is an active community of maintainers and a Special Interest Group ({{% wl "SIG" %}}) that forces a workable reference implementation of all things before they can be added to the language.  Unlike many other languages where a theoretical feature is added only to be poorly thought out, the SIG forces a working example to be implemented in a fork of the language before it is brought in.

This can make it frustrating for those familiar with other language constructs like package management, inheritance, or generics.  Go seems to move slowly and when picked the solutions don't always look like they do in other languages.  However, this is a strength of Go.  The solutions that Go comes up with scale extremely well because they are only added to the language if they do.

Take for example error handling in Go. It is implemented as an interface, where any object that has a function `Error() string` is considered an error. This means:

- Errors are treated as variables, and don't need special handling.
- Functions often return both an object and an error, leveraging Go's multiple-return feature. This encourages handling errors immediately after they are returned.

To check if a file is closed, you can use a simple comparison like `if err == io.EOF`, which checks if the error is exactly `io.EOF`.  `io.EOF` is a singleton defined in the `io` package.  So you are asking if the memory address of the error is that of `io.EOF`.  In many cases, when you know the context of the error, this is enough.

However, there are cases where the exact context isn't fully known, leading to much debate on how to handle these cases.  Go came up with the wrapped errors.  Functionally it acts kind of like exception inheritance in other languages.  Let's say you want to print the file name in the error, you would wrap the error: `return fmt.Errorf("file :%v, %w", file_name, io.EOF)`.  This breaks `err == io.EOF` since the new error is not `io.EOF`.  So two functions to check wrapped errors were added: `Is` and `As`.

```go
func usingIs() {
  if _, err := os.Open("non-existing"); err != nil {
    if errors.Is(err, io.ErrNotExist) {
      fmt.Println("File does not exist")
    }
  }
}

func usingAs() {
  if _, err := os.Open("non-existing"); err != nil {
    var pathError *fs.PathError
    if errors.AS(err, io.&pathError) {
      fmt.Println("Failed at Path:", pathError.Path)
    }
  }
}
```

which will check if the current error is or wraps `io.EOF`.  In this way it is a drop in replacement for `==`, plus works with error wrapping.
