---
title: Ruby on Rails
date: '2023-07-23'
lastmod: '2026-07-28'
draft: false
keywords:
- Ruby on Rails
params:
  garden:
    kind: item
    usefulness: hold
    category: code
    movement: No Change
    subcategories:
    - framework
---

[Ruby on Rails](https://rubyonrails.org/). Is a full-stack web framework built on [[Ruby]] that popularized convention-over-configuration, ActiveRecord as an [[ORM]], and [[MVC]] for server-rendered apps.

## Blurb

> A full-stack web application framework written in Ruby, following the Model View Controller pattern, that includes everything you need to build modern database-backed web apps.

## Summary

Rails proved that productive frameworks could ship real products quickly, scaffolding, migrations, and a cohesive standard library lowered the bar for web startups. That same cohesion becomes a liability when you need independent scaling of read/write paths, strict performance budgets, or polyglot services. Teams often discover too late that the fastest path forward is a partial strangler off Rails rather than incremental tuning inside it.

## Details

- **Strengths (historical):** rapid prototyping, strong conventions, batteries-included auth/jobs/mailers, large gem ecosystem.
- **Weaknesses (today):** global state and "magic" complicate reasoning; ActiveRecord encourages fat models; multi-process scaling and background work add operational cost compared to lighter stacks.
- **Operations:** legacy deployments often paired Rails with [[Capistrano]]
- **When hold is OK:** maintaining an existing Rails monolith with a committed team; greenfield work should default to stacks that match your expected scale and hiring pool (often not [[Ruby]]).
