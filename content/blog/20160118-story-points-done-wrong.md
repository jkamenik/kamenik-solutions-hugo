---
title: 'Story Points Done Wrong'
date: 2016-01-18
lastmod: 2016-01-18

# Keywords help in classifying content
keywords:
  - Story Points Done Wrong
---

Ever said or heard something like:

- "How many hours per Point?"
- "How many days is a 3 point story?"
- "Why can't we just use hours?"

If so...

![scrum-fail.jpg](/images/scrum-fail.jpg)

<!--more-->

To be honest Story Points are probably the trickiest part of Scrum largely because everyone "wants" them to be something that they are not. But once you understand them they are far more useful and accurate then any other form of estimation (that I have seen).

## Story Points are Complexity not Time

Story Point do not aim to be an accurate calendar representation of work. And because of this, when used correctly they are. Story Points are a measure of risk and complexity combined into a single number, nothing more and nothing less.

At most you should use 5 story point values, but ideally you have fewer. The scale you choose doesn't matter just so long as everyone knows that there is no direct relationship. For example, 2 smalls don't make a medium.

Points are chosen by comparing the unestimated story to a known golden story whose complexity is well understood. Finding the golden story is the hardest part of using Story Points, but also the most important. Usually it is best to pick a single generic medium story. That way the comparision is simply "is this story more effort, less effort, or similar effort to the golden story".

### Grooming: Never do Points at Planning

I won't go over what or how to do Grooming, but by the time planning starts it is already too late for Story Points to have value. Planning is the time where a story is tasked out and (if the teams so chooses) hours assigned to tasks. If you wait, then Points will be equated to hours and the value of Points is lost.

### Voting

Each team member should vote in silence and at the same time so they are not influenced by a dominate person (usually a PO or senior dev which under values complexity, effort, or risk). The idea is to get a general consensus, not a unanimous verdicts. If there is an event split or one extreme outlier, then a discussion should be had so that everyone understands. A new vote should be taken after the discussion. Repeat until everyone is close to the same number then pick the point value of the majority and move on.

## I Need a Time! - Velocity

By abstracting Points from Time you are no longer conflating the two. However, projects are done based on calendar time, so points need to be translate. Enter Velocity.

Velocity is simply the average number of Story Points the current team has done in the last several sprints. It doesn't pretend to have perfect knowledge. It is just a calculated number which accurately represents how the team produces.

On the small (at the sprint level) velocity has little to no accuracy, but on the large (at the release level) it is very accurate. Think of it like a radioactive half-life. At the atom level you have 0% chance of guessing when it will decay into the stable form. However, at a larger quantity you know exactly how many atoms will decay in the time period (just not which ones).

If you are used to moving warm bodies around, or individually assigning stories, then velocity may seem like a step backwards. And maybe you (or a manager) have even seen short term gains doing your own thing, but eventually things will turn sour (usually at the worst possible time). Go read [Mythical Man Month](https://en.wikipedia.org/wiki/The_Mythical_Man-Month), and return here when finished.

A stable velocity is a fragile thing, and it doesn't pretend like it isn't, but if you are willing to protect the team (and by extension the velocity) then it is amazingly accurate. For example, if over the last 3 sprints the team has averaged 10 points a sprint and you double the team size and put 20 points of work into the sprint then there is no hope of success because the velocity number is still 10 point / sprint.

Velocity changes slowly, so don't fall into the trap of playing with team makeup in an attempt to gain velocity. It is always better to increase throughput (amount of new feature) while leaving velocity alone.

### Throughput

Throughput is simply the number of new features added. It is related to velocity, but not the same. In fact, whenever someone says "we need to increase our velocity" this is actually what they mean. The easiest way to increase throughput is to limit risk in one of the following ways.

1. Cut scope
    1. Does "user login" imply a "forgot password" process? If so, split it into two explicit stories.
2. Cut stories horizontally
    1. Stories are often cut vertically, which usually leads to interesting half done features. Consider cutting stories horizontally first, then vertically. To ensure that stories aren't half done and need to be revisited.
3. Release Earlier - with an easy upgrade path
    1. A Min Viable Product is likely 2 to 3x more features then are actually needed. In many cases it is better to 1/2 the feature count and 2x the quality and release early. Remember, once you release you must support; which is going to chew up time, so get used to it.
4. Don't focus only on the "customer"
    1. A "user" is any user of the system including Devs (developers and QA). Making their jobs easier will increase throughput overall. So make sure stories reduce tech debt, and increase automation and testing.

### We overcommit

A very common problem, if you use Story Points at sprint planning is to overcommit the team. Like previously said, points have no accuracy in the small. So using them as a measure of the sprint will result in no accuracy.

Points may (and should be used) by the PO to help order the backlog so an even mix of large and small tasks make it into a sprint. If the sprint is mostly large stories (which are large because of risk or complexity) then the sprint is likely to fail.

The correct way to do planning is to take each story from the backlog and task it out. For each task add an estimated time to complete, and don't forget about QA or outside team tasks, but refrain from assigning tasks. Keep tasking stories until you get to the story that can only be partially completed during the sprint. The PO may decide to accept a half done story, or decide to rearrange the backlog to find a smaller story.

Once the stories are pulled into the sprint it is entirely up to the team to decide when and in what order to do the stories. Ideally, the entire team would bring a single story to completion before starting another, but there are cases where it doen't work completely. For those cases the devs should move on to testing.

When deciding how many tasks will fit in a sprint a good rule of thumb is 5 productive hours per day per person. This is because email, team discussions, and scrum meetings all take away from development time. The larger the team it more coordination is needed therefore 5 hours is only true for teams of 3 to 5 devs. For larger teams take away 45min of productive time per additional dev.
