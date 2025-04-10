---
title: 'ChatOps'
date: 2023-07-23
lastmod: 2023-07-23

# Keywords help in classifying content
keywords:
  - ChatOps
  - anti-pattern

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: hold

    # tools, techniques, platforms, languages & frameworks
    quadrant: techniques

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

ChatOps means two distinct things: 1) sending alerts to a chat application, and 2) using a bot to receive commands from a chat app. Chat apps like {{% wl "Slack" %}} strongly recommend this model. They even include hundreds (maybe thousands) of integrations specifically targeted at these use cases. However, for development work, this approach is often a mistake. It is either ignored or, more likely, slows the team down due to constant distractions.

It was and is strongly recommended by tools that are in the chat space like {{% wl "Slack" %}}.  However, in almost every case they are a bad idea and should be avoided for development work.  Thus we put ChatOps in the hold ring.  While it may be entertaining for generating memes, it is not suitable for critical tasks.

<!--more-->

## ChatOps for Alerting

In DevOps / DevSecOps alerting is very important.  It is the way that you know something is wrong and that your attention is actually needed.  You need to leave that space clear for only the most important alerts and thus mixing that type of alerting with co-worker chats is a bad idea.

## ChatOps for Actions

Triggering automation from a chat program seems like a boon.  Who wouldn't want to force encrypt all their drives right before they walk onto an air plane for a 5 hour trip...  Anyone in DevSecOps.

Also, it is really inadvisable to give your chat software access to your critical infrastructure.  Therefore any investment made in this area will quickly fail a standard audit leaving you with no viable path.  It is better to not fall in this trap to begin with.
