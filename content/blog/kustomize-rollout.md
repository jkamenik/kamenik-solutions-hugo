---
title: 'Kustomize Rollout'
date: 2025-04-18
lastmod: 2025-04-18

# Keywords help in classifying content
keywords:
  - Kustomize Rollout
  - kustomize
  - rollout
  - ab style
---

{{< wl Kustomize >}} is a tool built into `kubectl` which helps in the management of YAML.  It does a lot of things, but one of the major ones is having overlays per deployment.  It is not uncommon to have a single base and a rollout per deployments.  However, this can cause issue when you need to fix your base, as it will happily update all your overlaid environments en mass; which is less then ideal.  Here is how I have fixed that for my deployments.

<!--more-->

## Setup

Let's say we have the following kustomize layout.  It is a simple deployment with a service and ingress.  There are 4 deployments; the 3 standard stages (dev, staging, prod) plus a local testing overlay meant to be deployed manually to a local instance.

{{< filetree/container >}}
  {{< filetree/folder name="app" >}}
    {{< filetree/folder name="base" >}}
      {{< filetree/file name="deployment.yaml" >}}
      {{< filetree/file name="ingress.yaml" >}}
      {{< filetree/file name="kustomization.yaml" >}}
      {{< filetree/file name="service.yaml" >}}
    {{< /filetree/folder >}}

    {{< filetree/folder name="overlays" >}}
      {{< filetree/folder name="dev" >}}{{< filetree/file name="kustomization.yaml" >}}{{< /filetree/folder >}}
      {{< filetree/folder name="local" >}}{{< filetree/file name="kustomization.yaml" >}}{{< /filetree/folder >}}
      {{< filetree/folder name="prod" >}}{{< filetree/file name="kustomization.yaml" >}}{{< /filetree/folder >}}
      {{< filetree/folder name="staging" >}}{{< filetree/file name="kustomization.yaml" >}}{{< /filetree/folder >}}
    {{< /filetree/folder >}}
  {{< /filetree/folder >}}
{{< /filetree/container >}}

## Option 1: Patches

In this first option everything that makes a deployment unique is only tracked in the overlay via patches.  This is very good for simple patches like the following:

```yaml
# overlays/dev/kustomization.yaml
resources:
  - ../base

patches:
  - patch: |-
      - op: replace
        path: /spec/rules/0/host
        value: dev.example.com
    target:
      kind: Ingress
      name: app
```

However, things are little more annoying if you have to exclude or remote items.  There is no way in kustomize to delete entire objects so the only way to handle this in each overlay is via full object copies.  If however, you have a large discrepancy between an env or a lot of object then this can be error prone.

## Option 2: A/B Bases

> [!NOTE]
> This style is more complicated because it prevents accidental rollouts.  It should be reserved for when the deployment maturity requires it.

In this style the base has `a`, `b`, `provider-a` and `provider-b` bases as well as all the standard overlays plus a `local` overlay that cannot have provider specific objects.

{{< filetree/container >}}
  {{< filetree/folder name="app" >}}
    {{< filetree/folder name="base" >}}
      {{< filetree/folder name="a" >}}
        {{< filetree/file name="deployment.yaml" >}}
        {{< filetree/file name="ingress.yaml" >}}
        {{< filetree/file name="kustomization.yaml" >}}
        {{< filetree/file name="service.yaml" >}}
      {{< /filetree/folder >}}
      {{< filetree/folder name="provider-a" >}}
        {{< filetree/file name="backend-config.yaml" >}}
        {{< filetree/file name="cert.yaml" >}}
        {{< filetree/file name="external-secret.yaml" >}}
        {{< filetree/file name="frontend-config.yaml" >}}
        {{< filetree/file name="kustomization.yaml" >}}
      {{< /filetree/folder >}}

      {{< filetree/folder name="b" >}}
        {{< filetree/file name="deployment.yaml" >}}
        {{< filetree/file name="ingress.yaml" >}}
        {{< filetree/file name="kustomization.yaml" >}}
        {{< filetree/file name="service.yaml" >}}
      {{< /filetree/folder >}}
      {{< filetree/folder name="provider-b" >}}
        {{< filetree/file name="backend-config.yaml" >}}
        {{< filetree/file name="cert.yaml" >}}
        {{< filetree/file name="external-secret.yaml" >}}
        {{< filetree/file name="frontend-config.yaml" >}}
        {{< filetree/file name="kustomization.yaml" >}}
      {{< /filetree/folder >}}
    {{< /filetree/folder >}}

    {{< filetree/folder name="overlays" >}}
      {{< filetree/folder name="dev" >}}{{< filetree/file name="kustomization.yaml" >}}{{< /filetree/folder >}}
      {{< filetree/folder name="local" >}}{{< filetree/file name="kustomization.yaml" >}}{{< /filetree/folder >}}
      {{< filetree/folder name="prod" >}}{{< filetree/file name="kustomization.yaml" >}}{{< /filetree/folder >}}
      {{< filetree/folder name="staging" >}}{{< filetree/file name="kustomization.yaml" >}}{{< /filetree/folder >}}
    {{< /filetree/folder >}}
  {{< /filetree/folder >}}
{{< /filetree/container >}}

A standard rollout is as follows:

1. Every overlay is pointing at `*a`
    1. `local` and `provider-a` directly at `a`
    1. `dev`, `staging`, and `prod` at `provider-a`
1. Create / update `b` to be what is in `a`
1. Point `local` to `b`
1. Update `b` until it works for `local`
1. Create / update `provider-b` based on `provider-a`
    1. Make sure that `provider-b` points to `b`
1. Point `dev` to `provider-b`
1. Update `provider-b` until it works for `dev`
1. Roll out the changes to `staging` and `prod`
1. (optional) Delete `a` and `provider-a`

> [!WARNING] Blast Radius Diff
> Because there are going to be so many file changes with every update it is useful to create a script that can diff the output of kustomize between what is currently deployed (usually the `main` branch), and what is currently on the branch.  This is the only way to get a real idea of the blast radius of the change.

## Option 3: Versioned Helm Charts

The final option - which is complicated as it introduces a new tool - is to produce a versioned {{< wl "helm chart" >}}.  Then use that reference and a values file in each overlay.  In this case, because the helm chart is the base, no separate base is needed.

{{< filetree/container >}}
  {{< filetree/folder name="app" >}}
    {{< filetree/folder name="overlays" >}}
      {{< filetree/folder name="dev" >}}
        {{< filetree/file name="kustomization.yaml" >}}
        {{< filetree/file name="values.yaml" >}}
      {{< /filetree/folder >}}
      {{< filetree/folder name="local" >}}
        {{< filetree/file name="kustomization.yaml" >}}
        {{< filetree/file name="values.yaml" >}}
      {{< /filetree/folder >}}
      {{< filetree/folder name="prod" >}}
        {{< filetree/file name="kustomization.yaml" >}}
        {{< filetree/file name="values.yaml" >}}
      {{< /filetree/folder >}}
      {{< filetree/folder name="staging" >}}
        {{< filetree/file name="kustomization.yaml" >}}
        {{< filetree/file name="values.yaml" >}}
      {{< /filetree/folder >}}
    {{< /filetree/folder >}}
  {{< /filetree/folder >}}
{{< /filetree/container >}}

Each `kustomizaton.yaml` would look like this:

```yaml
helmCharts:
- name: app
  includeCRDs: false
  valuesFile: values.yaml
  version: 3.1.3
  repo: https://oci.example.com/repos/app
```

Separately you will need a repo for the helm chart with a CI pipeline that pushes a versioned OCI image to a repository.  To rollout a change you update the `version` flag and make any correction needed to the values file.

> [!NOTE]
> It is not uncommon to do local testing directly from the Helm chart and have a special dev cluster for manually testing the helm chart before it gets rolled out.  This means that the local vs provider specific objects has to handled by logic exposed in the `values.yaml`.
>
> ```yaml
> # values.yaml
> provider: "local" # only include the CRDs valid for local deployments
> # or provide explitic disable flags
> disableExternalSecrets: true
> disableManagedCertificates: true
>
> # hardcoded secrets are now needed
> secrets:
>   someSecret:
>     key: some-secret-value
> ```

> [!ERROR] Don't use `chartHome`
> Kustomize does support a `chartHome` option which will use a local file path to find the helm chart.  Don't use it, as it is worst of all worlds.  You have to manage it in A/B style or you have to add the stage logic to the chart directly which means you cannot truly test it before roll out.  It will bite you.
