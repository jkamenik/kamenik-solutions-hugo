---
title: "CUE"
date: 2025-07-10
lastmod: 2026-05-17
draft: false

keywords:
  - CUE

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"

aliases:
  - /radar/tools/cue
---

[CUE](https://cuelang.org) is a schema validating tool that also does code expansion / generation. It is a different take on [[Policy as Code]] and is made to provide generic guardrails in its own language format which can be translated into other ecosystem compliant formats like [[JSON Schema]], [[Protobuf]], or [[OpenAPI]].

While it is an interesting take on the problem, at this point in time, we don't recommend it as there aren't very compelling use cases. However, it might be just what you are looking for.

![XKCD 927](https://imgs.xkcd.com/comics/standards.png)

With all that being said, it is a good public demonstration of [Google's General Config Language (GCL)](https://pure.tue.nl/ws/portalfiles/portal/46927079/638953-1.pdf) language that is used internally to configure much of what Google does. You can see that influence deeply inside the Design of CUE, so even if you don't use CUE directly it is worth it a read.

Google needed a way to write configurations that could be easily expanded and lightly validated. These configurations would be entirely private to Google, so there was no need to have a formal specification. In fact, separating the formal spec from validation and expansion would have been cumbersome. Their language defines a single format that can be used to generate and loosely validate configurations of any type that other systems needed, such as BorgCfn for Borg, JSON, XML, Protobuf, etc. The validations were not meant to be exhaustive, but rather to give programmers confidence that they were not making obvious mistakes. CUE is a public implementation of that idea.
