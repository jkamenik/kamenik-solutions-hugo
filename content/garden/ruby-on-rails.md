---
title: "Ruby on Rails"
date: 2023-07-23
lastmod: 2026-05-17
draft: false

keywords:
  - Ruby on Rails

params:
  garden:
    kind: item
    usefulness: hold
    category: code
    movement: "No Change"
    subcategories:
      - framework

aliases:
---

[Ruby on Rails](https://rubyonrails.org/) is a full-stack web framework built on [[Ruby]] that popularized convention-over-configuration, ActiveRecord as an [[ORM]], and [[MVC]] for server-rendered apps. It made CRUD and early SaaS prototypes fast in the 2000s, but we rate it **hold** for new work: scaling and team velocity usually require peeling off the framework's opinions long before the product is mature.

## Blurb

> Rails is a web-application framework that includes everything needed to create database-backed web applications according to the Model-View-Controller (MVC) pattern.

## Summary

Rails proved that productive frameworks could ship real products quickly—scaffolding, migrations, and a cohesive standard library lowered the bar for web startups. That same cohesion becomes a liability when you need independent scaling of read/write paths, strict performance budgets, or polyglot services. Teams often discover too late that the fastest path forward is a partial strangler off Rails rather than incremental tuning inside it.

## Details

- **Strengths (historical):** rapid prototyping, strong conventions, batteries-included auth/jobs/mailers, large gem ecosystem.
- **Weaknesses (today):** global state and "magic" complicate reasoning; ActiveRecord encourages fat models; multi-process scaling and background work add operational cost compared to lighter stacks.
- **Operations:** legacy deployments often paired Rails with [[Capistrano]]; local dev tools like [[Pow]] addressed Rack host naming before modern DNS helpers.
- **When hold is OK:** maintaining an existing Rails monolith with a committed team; greenfield work should default to stacks that match your expected scale and hiring pool (often not [[Ruby]]).
