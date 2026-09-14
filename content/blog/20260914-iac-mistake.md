---
title: 'Is IaC a Mistake'
date: 2026-09-14
lastmod: 2026-09-14
keywords:
  - IaC
---

I have been in and around infrastructure automation for a long time.  Longer than I care to discuss.  And every few years I have noticed a pattern.  That is a new tool to do the exact same thing as older tools while handwaving what is actually important.

There has to be a better way, right?  I am concerned that with all the benefits of IaC we still are no closer to solving the actual problem that leads us to pick up IaC in the first place.

<!-- more -->

## Background: SNMP & NCCM

When I started in the industry what we had was Telnet (`ssh` wasn't widespread yet) and Simple Network Management Protocol (SNMP).  SNMP was a universal protocol that was supposed to allow you to configure any network device.  It did this by making every single configuration option an individually addressable Object ID (OID) in a tree structure.  Everyone was supposed to map to a common set of OIDs, but they allowed each vendor to have a section of the tree to call their own.

There were many issues with this level of abstraction as a true management protocol, which was mostly due to the complexity of rules needed in setting the related OID values.  Usually, hundreds to tens of thousands of OID values had to be set per device managed.  But the OID would often change between versions and every new feature has a new tree of OIDs.  It was so low-level and raw that it became almost useless as a management language.

As an aside, many current machines (possibly even the machine you're using to access the internet) have SNMP enabled (albeit read-only).  While its use for management isn't common anymore, it is still very commonly used for monitoring.

At the company I was working at we took a page out of Cisco's and Juniper's playbook and made our OIDs read-only, and standardizing on a Cisco-style terminal configuration language as the only means of configuring the device.  This had the benefit of allowing a single configuration command to be complex - often setting dozens of OIDs at once.  It moved items up a level of abstraction making management easier.  It also made our boot process substantially easier as a simple matter of replaying a configuration file as if the user was typing it.  This gave us much better control over validation while also adding additional virtual "super" commands that did a lot of things all at once in the correct order.

However, even that was not enough because rarely does a single device live on its own.  These devices had to work together.  This meant what you really needed was something that could configure multiple devices at the same time.  Many vendors provided a vendor specific control plane tool for this and that company was no different.  I wrote a backplane manager which was a GUI program where you draw the rack of devices and how they were connected.  It would suck in their configurations and then validate them operationally against network flow.  Green was good, and Red meant a misconfiguration.  You could then inspect and fix the configuration in the simulator before pushing it back to the devices.

Unfortunately, this only worked for a small subset of our devices and only for a specific set of their configurations that were related to our validation rules.  Sure we could add additional devices and configuration support over time, but the customer could not.

The next company I worked for created a vendor agnostic tool and a Gartner market segment called Network Change and Configuration Management (NCCM).  The goal was to control a fleet of network devices regardless of vendor.  At that time we standardized on Telnet terminal invocation and later expanded to SSH and storing the text based configuration.  Basically, using our tool a network engineer should execute a single command or even a series of commands across a fleet of devices.  However, in hindsight this was a misstep because we focused on how and not why.  Therefore, all our features were related to making configuration easier to manage, but didn't do anything to solve the underlying problem.

## Determinism & IaC

Many years after NCCM came the cloud.  And with the Cloud came outcome-based APIs.  No longer did you have to care about the specific switch port configuration.  Instead, you cared about the higher-layer constructs like virtual networks, subnet, and compute.  You asked for what you needed, and left it to the provider to figure out the details.

Even that is in some cases too low-level.  In many cases we need a higher-level operational construct like scaling, disaster recovery, and upgrades.  This concept of letting the provider figure out the details has since extended into the tooling making [[IaC]] the default.  There are pure declarative IaC tools like [[Terraform]] and [[Kubernetes]] which make it very difficult to do non-declarative things.  And there are hybrid tools like [[Ansible]] which prefer declarative IaC, but do allow for non-declarative scripts to be run for the edge cases.

This is a step in the right direction, but not nearly enough for true automation.  Not only that, but their architectural choices themselves cause issues that have to be overcome.

## The Real Issues: Drift, Shadow IaC, Day 2, and Purpose

For all the benefits of IaC tooling it has exposed several weaknesses.

### Drift
IaC tooling is generally one-shot, not continuous.  That means it only runs a reconciliation cycle when instructed to do so.  In between two cycles it is easy for the natural changes of the environment to become out-of-sync with the IaC.

Additionally, during emergencies, IaC tools are often avoided because they are outside the debugging cycle.  In the best case this is state that can be reconciled back into the IaC's state; though it usually takes a lot of effort sometimes more than the value of the change.

### Shadow IaC
In IT whenever there is a tool or system used that isn't officially known by the IT department it is known as Shadow IT.  This introduces the scariest kind of risk; unknown risk.

IaC has a similar issue.  That is, during the natural course of maintenance things in the infrastructure change.  Many times these are changes to objects and configuration tracked by IaC.  In this case we call it drift and we know about it.

However, often these are changes in objects that are not known to IaC.  We call this shadow IaC and it is a far bigger problem than drift because it is unknown.  And once known it is often difficult to add the references to IaC in a perfectly compatible way.

### Day 2
"Day 2" is operational shorthand for all the on-going maintenance that is required to keep something running.  Day 2 issues are what cause Drift and Shadow IaC, but the real question is why.  And by and large the reason is that even though IaC is supposed to be declarative (I want an encrypted disk, instead of here are the steps to create an encrypted disk), the reality is often far from it.

I often give the example of setting encryption on an EBS volume.  By default EBS volumes have no encryption unless you explicitly set the encryption flag(s).  You have the choice between provider and customer managed keys.  However, the issue is that any change to the encryption setting removes the existing disk and replaces it with an empty disk.  This is a non-obvious outcome, but obviously not the intent.  This is the kind of thing only an operations expert would know.

In this example IaC tooling actually gets in the way because to encrypt a disk requires a bunch of manual steps.  So effectively, depending on the IaC tooling chosen, you have to disable the tooling, fix the underlying issue manually (encrypt the disk), and verify it manually.  Then reverse those changes manually back into new IaC objects (usually this requires forking golden modules), then update the existing state to match reality again, and finally re-enable the IaC tooling.  The entire time you spend convincing yourself that this effort is worth it.

### Purpose
While IaC is great at declaring objects and configuration it completely lacks purpose.  This purpose, if it exists at all, is left to tools that manage the IaC files (often git commit messages) or the tools that drove the tasking (Jira or ServiceNow).  It isn't nothing, but isn't first class either.

I cannot express how many times in my career my debugging consisted of trying to glean the purpose of a change. I needed to determine if the change was on-purpose with good reason, on-purpose as a mistake, or just plain wrong.  With the intent buried and separate this task is made difficult, often impossible.

## What Is Next? Intent-as-a-Service

Basically the biggest issues are really:

1. Lack of Expertise
2. Incomplete Solutions
3. Missing Abstractions

However, I think they can all be solved with reframing around **intent**.  As they say in the legal profession "intent is everything".  That is really the thing that is missing.  This is not a new concept.  Many years ago Google released a white-paper titled [Prodspec and Annealing](https://www.usenix.org/publications/loginonline/prodspec-and-annealing-intent-based-actuation-google-production).  In that paper they explained the process by which intent (the prodspec) becomes reality (annealing).  Many years on and many of those lessons have become the basis of Kubernetes.  There is even now a K8s SIG called [[Crossplane]] which aims to use K8s objects to control any infrastructure.

This is a step in the right direction in that the expertise is bundled into an operator that continually monitors the infrastructure.  This solves drift entirely.  It also probably solves Shadow IaC as well.  The only real thing missing is tracking the intent of changes to the configuration itself and the necessary ad-hoc workflows that have to be applied along with changes to the infrastructure.

What everyone really needs is an orchestrator that sits on top of a system like [[Crossplane]] that specifically tracks day-2 concerns via intent.  A so-called Intent-as-a-Service system.  So for example you'd say, "Encrypt EBS volumes with provider managed keys".  Out from that would flow any changes to the IaC, but also any operational playbooks that are needed like backing up the volume so data can be copied.  The more that is done at the infrastructure level the less has to be via operational playbooks, but there will likely always be a need to have those so they need to be first class.

What you get at the end should be a changelog of all the requested changes over the life of the system.  And if done correctly the intent-based changelog becomes the verification procedure, so the system can self monitor that the intent was fulfilled.

The expertise can be concentrated into the annealer / operator that does the monitoring and reconciliation of infrastructure.  Its sole job is to drive the removal of drift between the intent and reality.  The orchestrator on top would then coordinate across annealers and providers to make sure the final state is reached and maintained.  Loops of loops.

That is the dream.  And with AI that dream might be closer than ever before.
