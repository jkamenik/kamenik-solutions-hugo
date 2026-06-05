---
title: 'Curating Personal Agent Skills'
date: 2026-06-05
lastmod: 2026-06-05

# Keywords help in classifying content
keywords:
  - Agent Skills
  - AI
  - MCP
  - Developer Experience
---
I have been using AI for many years, and within the last year really got heavy into [[MCP]] and [[Agent Skills Framework]]. At this point it is clear that using agents is now a required skill by any engineer and many (if not most) non-engineering jobs.

The thing that is going to separate the haves and have-nots in this new reality is the curated list of personal Agent skills you develop and take with you. Here I am going to explain how to do that successfully.

<!--more-->

First, I am going to assume you are familiar with AI Agents, and how your particular agent framework loads skills. There are many ways this is done but at the end of the day it boils down to a directory that contains an `AGENTS.md` (or `CLAUDE.md` because Anthropic uses that name) and a `skills` directory of directories containing `SKILL.md` files. That directory is the one you need to manage and maintain.

## A Soul

The first thing you need to do is give your Agent a Soul. The `SOUL.md` gives your agent a purpose, and rules for how it behaves with you. Start small and define these things:

- Your Identity - How do you think of yourself (i.e. "I am …")
- Its Identity - How should it know itself (does it have a name? Should it be an employee of yours? Should it pretend to be you?)
- Communication Style - How you like to be talked to (i.e., "Concise with a lot of links backing up your statements")
- Operating Principles - What MUST the agent do, what MUST it NOT do

## First: Tool-Skills and MCPs

The very next thing is to load a few tool-based skills. These tell the agent how it can do things. I keep a fairly up to date curated list of [[Agent Skills - Sources|Agent Skills]] to pull from. First you should look for tool-skills which are basic and portable skills like [`apple-reminders`](https://hermes-agent.nousresearch.com/docs/user-guide/skills/bundled/apple/apple-apple-reminders).

Add one or two you think will be useful, and run them to see if there is additional setup that is needed (usually auth tokens and MCP servers). Once you have a basic conversation and get the agent to do a thing it is time to open the floodgates, and let the agent maintain itself.

### Understand Skill Types

There are no hard and fast rules with skills (because there is no standard). However, I like to think about skills as existing in one of three camps. They are:

1. Capability Skills - These teach the Agent to do a thing (like interface with apple reminders). They are highly portable, and can often be useful to others.
    1. Name these for what they do (i.e., `apple-reminders`, `proofread`)
2. Behavioral Skills - These teach the agent how to behave when using other skills (like using GTD when managing reminders).
    1. Name these for what they layer on top of (i.e., `reminders-gtd`, `proofread-blog`)
3. Domain Skills - These are outcome based skills that you define that reference the other skill types. These are highly specific to you.
    1. Name these for what they do (i.e., `morning-briefing`, `company-research`)

## Skillify Skill

The first real skill you need is the skill that can maintain skills for you. As meta as it sounds it is straightforward to create this skill via a conversation with the agent.

Create the stub skill as follows:

```yaml
---
name: skillify
description: "Create, improve, and audit SKILL.md. Use when building a new skill from scratch, refining an existing skill's description or commands, or auditing all skills for quality and staleness."
---
# Skillify
```

Then ask the agent to `create this skill based on the description`. Or even `using <path to my list of skills repos> create this skill.`. Just continue until you have something that looks like it should work. Then use it.

## Create Your Own `soul-audit` Skill

Now comes the first in a long line of skills you'll create: the `soul-audit`. Your agent's SOUL is critical to your success. So you need a skill that can specifically manage it; and it is a great test of your `skillify` skill.

```markdown
/skillify create soul-audit. I want to periodically update your soul (AGENTS.md) through a series of prompts. It should be re-runnable anytime to update any section of the soul. Use when I specifically ask for a soul-audit to be performed.
```

Your skill will be specific to you. But I like to keep my sections separate so it is easier for each phase to only update its section. My `AGENTS.md` looks like this:

```markdown
# AGENTS.md

Load the following in order:
- SOUL.md
- USER.md
- IDENTITY.md
- ACCESS_POLICY.md
```

Then my skill looks something like this:

```markdown
# SOUL Audit

Generate the agent's identity and operational configuration through an interactive interview. Each phase produces a file. Any phase can be re-run independently to update.

**IMPORTANT:** This skill generates content from the USER'S OWN ANSWERS. It NEVER ships pre-filled content.

## Phases

### Phase 1: Identity Interview
Ask: "What is this agent to you? Research partner? Executive assistant? Thinking partner? All of the above?"
Generate: SOUL.md identity section.

### Phase 2: Vibe Calibration
Show 3-4 communication style examples:
- **Formal:** "I've prepared a comprehensive analysis of the situation..."
- **Direct:** "Here's what's happening. Three things matter."
- **Technical:** "The root cause is in the connection pooling. Here's the fix."
- **Casual:** "Yeah so basically the thing is broken because X. Easy fix."
Ask which feels right.
Generate: SOUL.md vibe + communication style sections.

...
```

Once it is there, run it via `/soul-audit`.

## Conclusion

In our new AI-driven world your critical skill is being able to maintain a curated list of Agent Skills that is unique to how you work. This MUST be continually updated and maintained, so the first set of skills helps you do that. From there build out as you need to.
