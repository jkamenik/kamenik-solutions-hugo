---
title: 'Yaml'
date: 2025-04-09
lastmod: 2025-04-24

# Keywords help in classifying content
keywords:
  - Yaml
  - Yet another markup language
  - JSON

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

[YAML](https://yaml.org/) is a more human readable format which is fully API compatible with {{% wl "JSON" %}}.  It gained popularity as being the {{% wl "Declarative IaC" %}} language for things like {{% wl "Docker Compose" %}}, and {{% wl "Kubernetes" %}}.

There are some syntactic sugar like anchors and aliases and deep merging of maps which makes it easier to for humans to read.  Additionally, many systems (like {{% wl "Helm" %}}) add a templating language on-top to make generating large amounts of YAML easier.  And since Yaml is a subset of {{% wl "JSON" %}}, {{% wl "JSON Schema" %}} that can be used to validate complex YAML.  Because of this ubiquity you should adopt it.

<!--more-->

The creators of YAML also created {{% wl "YAMLScript" %}} as a templating language, but it is not wide spread yet.
