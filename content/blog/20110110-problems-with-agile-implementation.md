---
title: 'Problems With Agile Implementation'
date: 2011-01-10
lastmod: 2011-01-10

# Keywords help in classifying content
keywords:
  - Problems With Agile Implementation
  - Agile
  - HowTo
---

I really like agile programming. It keeps me close to the action, and makes me have to think about my next moves. It also keeps me informed as to what is going on around me. But in my many years of using agile I realize that, though the process itself is very nice, its implementations can tend not to be.

Problem don't arise from agile itself, but who and how it was implemented. If the implementer's goals do not match the [Agile Manifesto](http://en.wikipedia.org/wiki/Agile_software_development) there is little chance of success.

<!--more-->

I have used [scrum](https://en.wikipedia.org/wiki/Scrum_(software_development)) many times and the most common problems I see are:

## Agile as Micromanagement

There are many reasons that folks micromanage, but usually it comes from a place of fear. This fear then leads to an over involvement, which in turn leads to the Agile methods becoming a weapon for them to alleviate that fear by remaining in control.

**It looks like:**

1. Having to break task down into hourly segments of work
2. Having to break task that logically have to be done by a single person
3. Having to account for ALL time taken, even time not related to code like attending meetings
4. Having to be overly detailed in comments on work items
5. Using deadlines instead of priority

**Agile tenet misused:**

1. Individuals and interactions over process and tools
2. Working software over comprehensive documentation

This happens when a manager ([chicken role](http://en.wikipedia.org/wiki/Scrum_(development%5C)#.E2.80.9CChicken.E2.80.9D_roles)) is the Scrum Master or when the Product Owner has say over implementation specifics. It is a confusion of roles, which in turn leads to a confusion of goals, which in turn leads lost productivity.

## Agile as a Whip

Where micromanagement affects entire teams whips are an individualized weapon. Agile tools can be used to single out individuals just as well if not better than entire teams. The following are signs that it being to whip and individual.

**It looks like:**

1. Filtering a burn-down on an individual basis
2. Placing "realistic efforts" on tickets because the individual "cannot estimate correctly"
3. Associating points with people (publicly)
4. Associating number of tasks done with effort
5. Associating points with hours, in an attempt to estimate a person's working day
6. Basically anything where measured output is more important then people

**Agile tenet misused:**

1. Individuals and interactions over process and tools

Anytime you associate numbers with people you have created a [crab mentality](http://en.wikipedia.org/wiki/Crab_mentality). Their focus will stop being on software, but on making their numbers better. Those that are better at number games will succeed, those that are better at software will fail.

Anytime you put your people under undo pressure then simple mistakes are made. This is going to later erode confidence in the team. It is going to happen like this: "you missed a comma in a Javascript file which causes it not to work in IE. That was such a simple mistake to have tested for that I am not sure you are testing any of your code." The problem was caused by 4 hours of sleep in 72 hours of coding at the end of an over-extended sprint. The programmer was nearly delirious. It is shocking it was the only mistake, not that it was a simple mistake!

Unfortunately I have seen this situation start innocent enough, with comments like "we don't want to over work the staff" or "we want to make sure they always have something to do" or "we want them working on the correct things". If the "we" in question is management then there is probably already a misalignment, and Agile is going to be used as whip to solve the problems created by the bad implementation.

## Agile as Demotivation

And now we come full circle to have to do when Agile has been used poorly and management is stuck. Clearly it isn't Agile's fault cause Agile is perfect right?

What happens here is that management is try to convince folks that it is their fault. The following are some actual quotes I have been told over my career. I paraphrased to remove details about the person and companies involved.

**It looks like:**

1. "You said it would take 3 days. It took 10 days. You need to make up the difference out of your own time"
    1. It did actually only took 3 effort days, just took 10 calendar days due to distractions.
2. "We cannot slip these date, and you have already pared back the release 2 sprints ago. You need to put in extra effort"
    1. 2 Sprints ago the direction changed and 2 sprints of effort were exchanged with 2 others without discussion. It took 1 sprint to cleanup / hide the feature that were in-progress but that wasn't accounted for. There were still 2 sprints of effort left at this point
3. "Agile is about being agile. Even though we are mid sprint we are radically changing direction, we are not canceling the sprint or doing sprint planning. We are just swapping out some tasks for others. We already did the estimates for you so you can keep working."
    1. Yes, this was what was actually said to us those 2 sprints ago.

**Agile tenet misused:**

1. Individuals and interactions over process and tools
2. Responding to change over following a plan

These are all excuses I have heard. Each time given by a person in a manager role because they are ignoring changes in the field (military term). Every choice has a set of outcomes: some good, some bad. The attempt with agile is not to mitigate bad outcomes, but to allow those outcomes to contribute to the overall direction.

Sometimes the bad outcome will be that something took too long, or that one language/tool was not the correct choice given the problem set. If for every problem that happens the developer has to take their own time, or face embarrassment, to solve the problem then they will stop making choices. Not just choices that might have bad outcomes, but choices altogether. At which point someone in a management will start making detrimental choices.
