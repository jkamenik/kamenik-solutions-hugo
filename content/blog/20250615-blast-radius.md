---
title: 'Blast Radius - Critical Context'
date: 2025-06-15
lastmod: 2025-06-15

params:
  math: true

# Keywords help in classifying content
keywords:
  - Blast Radius
  - Security
  - Context
  - Key Performance Indicator
  - KPI
---

Context is everything, and understanding Blast Radius is crucial for providing the necessary context when assessing risk as a DevSecOps professional.

Blast Radius - simply put - is how much of the infrastructure is touched when a change is made.  The higher the blast radius the higher the risk.  And in the world of IaC that usually means it is caused by a change in IaC code.  So it would be natural to assume that a large change in blast radius would be caused by a large change in IaC, but that is often not the case.  There is only an indirect relationship between IaC lines changes and infrastructure changes.

But how do you protect yourself?

<!--more-->

You measure blast radius, then track it using Key Performance Indicator (KPI), and finally design to minimize it.

## Measuring Blast Radius

The best way to measure Blast Radius is by using the IaC tool itself.  A naive approach is to simply count the number of changes.  However, that doesn't include any kind of risk assessment.  Different types of change represent different risks.  Therefore, my recommendation is to calculate it as follows:

1. `+1` for any item added or deleted, but not replaced
    1. If possible, consider the underlying provider's objects and not what is in IaC.  For example, in terraform an `aws_s3_bucket` might have a `logging` block.  Those are 2 separate objects in AWS and thus should be counted separately.  As a side note, this is why the `logging` block is deprecated and the `aws_s3_bucket_logging` object should be used instead.
2. `+3` for any item changed in place
    1. They are higher risk targets as they are presumably already in place and working so a change is a higher risk
3. `+5` for any item that is replaced.
    1. They are already working, and any replace is likely to result in data loss.

Add up all the changes and that represents the risk of the change.  This can then be tracked over time to indicate the relative risk of changes.

### Optional items

The following items are harder to know because sometimes the IaC won't know.  But if you can track them, you should.

1. `+7` for any case where the IaC change would not be respected.  That is, the IaC is changed, but it won't effect the underlying infrastructure.
    1. If this doesn't result in an error then the IaC tool then it is a really high risk because you'll assume everything is ok, but it very much isn't.
    2. S3 bucket encryption is an example of this.  If the flag is enabled only new files are encrypted.  Older files remain unencrypted without any way to know.
2. `+9` if the change would cause loss of data
    1. This usually is only discovered during that oh-shit moment when everything fails and you have to trigger {{% wl "Disaster Recovery" %}}.  Once this type of change is known it should be documented as the kind of change that shouldn't be made.  {{% wl "Policy-as-Code" %}} tools are good for preventing this.
    2. At the time of this writing, {{% wl "AWS" %}} EFS encryption is an example.  It would happily remove all existing files when this flag is changed.

## Blast Radius KPI

The following are the KPIs you need to track and publish:

1. Blast Radius (See above) - This tells you the risk of each apply
2. IaC lines changed - This tells you the programmer's intended number of changes for each apply.  It is important to track the lines changed between two applies of the IaC, not just the lines changed per commit.
    1. Each line changed, added, or deleted counts as `+1`.
3. Resources Under Management (RUM) - This is a count of the number of objects described by the IaC at the time it is applied.  Since IaC often has means to reduce code duplication (like modules) this should be based on fully expanded resources, not just what is in the IaC files.
4. IaC Code Efficiency ($\frac{IaC\ resources}{1K\ line\ of\ code}$) - The number of resources should be at the plan or apply stage. The lines of code should be measured based on the workspace.  It is measuring how effective you are at using coding techniques to manage your IaC resources.
5. Change Risk (min, max, mean, median, & mode of $\frac{Blast\ Radius}{IaC\ Changes}$) - This tells you how much of your infrastructure is changing per change in IaC.  High numbers indicate that relative small changes in actual code cause high changes in infrastructure.

You need to balance IaC Code Efficiency and Change Risk to maximize your operational speed.

## Designing for Blast Damage

Each situation and business model is different.  So there is no one size-fits-all solution here.  The design goal should be to know what the maximum potential effect of a change could be and to ensure it is within an acceptable tolerance given the business.  Then design an IaC layout and processes that maximizes the IaC Code Efficiency without increasing the potential blast radius outside acceptable tolerances.

Balancing these two competing ideas is difficult and constantly needs to be revisited and adjusted.  Below are some ideas that might help you.

### Simple Base

Let's say you're using a code gen tool like {{% wl "Kustomize" %}}.  This uses a `base` + `overlays`.  Let's say there are overlays for `dev`, `staging`, and `prod`.  Any change to `base` affects all envs, thus has a large blast radius.  Change to overlays only affect those overlays.  Therefore they have a smaller blast radius.

A good technique to reduce blast radius is to apply the changes to each overlay individually.  This maximally reduces Blast Radius by maximally increasing code duplication.  To reduce code duplication, once each overlay has all the changes, move them up into `base` so that any new envs also benefit.  The idea is to keep the `base` as simple and minimal as possible, and copy and paste the required changes between `overlays`.

You might even consider splitting your monolith across multiple bases so that each can release independently.

### A/B rollout

A more extreme version of the above - but ultimately easier to maintain - is an A/B style rollout.  Using the Kustomize example again, you'd create a second copy of `base` called `base-b`.  You'd modify it as needed and point each overlay to it in turn.  Once all overlays are pointed at `base-b` you can erase `base`.

You'd have as many bases as you'd have in-process rollouts up to a maximum of the number of envs you have.  Therefore it is important to track the roll outs carefully.

Care also has to be taken with PRs since the actual line change will look huge but the relative change will be small.

### Check-in Fully Rendered Code

Similar to the A/B style, but more broadly is to use code gen tools like {{% wl "CUE" %}} to maintain an easier to manage base template then fully render it out and check-in that code.  In this case the CI/CD pipeline should only ever run off the fully rendered code, and the developer controls what changes get committed and thus the blast radius.

For early teams this is likely a good balance.  But as the team scales the amount of generated IaC per small change will be untenable.  So just keep that in mind.  This model is ultimately a path with limited long-term scalability (an "evolutionary dead-end"), but it could serve you for years before any issues arise.

### Versioned Artifacts

The most effective approach to handling Blast Radius is through the use of Versioned Artifacts and rolling out new versions. All roads will eventually lead to this method; however, there is quite a bit of effort involved in setting up a repository for the artifact, CI pipelines that include adequate testing, and artifact storage.

While this gives you the benefit of being able to independently test the artifact before release, the entire process does involve some amount of operational overhead.  Therefore it is only recommended for mature organizations for the items that MUST remain stable.

### Branches and/or Tags

Sort of a lazy man's versioned artifacts is using branches or tags.  Code can be merged between branches as needed to rollout changes, but you do not have to do things like setting up new repos, CI pipelines, or Artifact Repos.  Folks also generally know how to merge between branches better then they understand how to release artifacts.  Therefore it is a smaller conceptual load and easier to pick up.

However, there are some major downsides:

1. Merging is manual so forgetting to merge changes across branches will be common.
2. There is no relationship between branches, thus it won't be clear what or how changes can and should be made, or where things are deployed.
3. It would be entirely possible to have changes not flow though a standardized process.
4. Environments will tend to drift both making future merging difficult.
