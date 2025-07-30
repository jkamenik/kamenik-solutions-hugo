---
title: 'Go Concurrency Patterns'
date: 2014-10-17
lastmod: 2014-10-17

# Keywords help in classifying content
keywords:
  - Go Concurrency Patterns
  - Go
  - Golang
  - Concurrency
  - Programming
  - Patterns
---

One of Golang's strengths is its composability. This strength is only useful if you know how to make those composable parts. That is where patterns are useful.

Golang is concurrent, which is not necessarily parallel. However, to make things concurrent you have to break thing into atomic steps. If you are careful in how two step share information then you can easily turn concurrent design into parallel design. Go channels make this communication stupid simple, and thus make concurrent design very easy.

In this post I am going to share what I think are the basis of most other concurrency patterns: The Generator, The Worker, and The Consumer.


<!--more-->

## A note about parallel vs concurrent

Before we start, it might be useful to separate parallel and concurrent. Parallel is doing multiple things (usually the same or similar things) at the same time. Concurrent is doing multiple disparate things to converge on the same point. In other words, the purpose of concurrency to arrive at a solution, while parallel allows us to repeated arrive at a solution in the same span of time.

Another way to think of it is commuting to work, vs working. We all drive to work in parallel. However, at work our work is concurrently producing company value.

So why is this useful? OSes since the early days of Unix were parallel; they were routing phone calls after all, which is just a lot of the same thing. This in-turn meant that the OS level abstractions (threads and processes) were parallel and no thought was given to concurrent abstractions.

This in-turn was exposed directly by most programming languages. However, just as driving to work doesn't necessarily make you useful these constructs on their own isn't useful. Additionally, there are a lot of edge cases and paradoxes when parallel code tries to become concurrent.

However, properly concurrent code can become parallel code quite easily. Go luckily allows us to structure our code concurrently and then handles the parallelism without you having to use a thread.

Below are the basic types of concurrent actions. If you keep your code bitesized and focused then parallelism is automatic.

## The Generator

A generator simply does work and places that work on a channel. What that means is really up to what is needed but the pattern is:

1. Create a channel
2. Create closure which does work
3. Execute the closure as a goroutine, closing the channel when done
4. Return the channel

```go
func generateInt() chan int32 {
  // 1. Create a channel
  out := make(chan int32)

  // 3. Spawn a closure
  go func(){
    defer close(out)

    // 2. Do work
    for i := int32(0); i < 100; i++ {
      out <- i
    }
  }()

  // 4. Return the channel
  return out
}
```

## The Worker

A worker takes stuff off an input channel, works on it, and places the result on an output channel.

```go
func enlargeInt(in chan int32) chan int32 {
  out := make(chan int32)

  go func() {
    defer close(out)

    for x := range(in) {
      out <- x*2
    }
  }()

  return out
}
```

## The Consumer

A consumer takes stuff off an input channel and consumes it. There are two primary way to do this: Blocker and Signaller.

### Blocker

The blocker form simply run the code. This version is useful if there is a main loop which shouldn't exit until all work is complete.

```go
func printInt(in chan int32) {
  for x := range(in) {
    fmt.Println(x)
  }
}
```

[Here is a full working version.](http://play.golang.org/p/7Iz7kV7soo)

### Signaller

A signaller is actually a varient of the Worker pattern, where the output channel is used to signal the completion of work.

```go
func printInt(in chan int32) chan bool {
  out := make(chan bool)

  go func() {
    defer close(out)

    // Work until the channel is closed
    for x := range(in) {
      fmt.Println(x)
    }

    // Single that I am done
    out <- true
  }()

  return out
}
```

[Here is a full working version.](http://play.golang.org/p/1LIgv1ULDy)
