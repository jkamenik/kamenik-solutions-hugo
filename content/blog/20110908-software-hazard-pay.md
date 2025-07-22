---
title: 'Software Hazard Pay'
date: 2011-09-08
lastmod: 2011-09-08

# Keywords help in classifying content
keywords:
  - Software Hazard Pay
  - Rant
  - Opinion
---

The military has a concept of "hazard pay" which is extra money because you are placing your life on the line. Software has something similar, though certainly not as permanent, where you are putting your socioeconomic well being on the line.

The following is a list of things that I think are software hazards that should require more pay.

<!--more-->

## Dress-code Policy

A policy is an explicit rule created to cover an anomaly. And when the anomaly is repaired the policy remains. Dress-code policies ("dress atire shall be no less then business casual") like social-conduct policies ("you shall report yourself in a professional manner") are specifically vague, as to leave management leeway so that enforcement is discretionary.

I am against these type of policys because they setup a confrontational attitude between management and workers. I personally do not know of any professional (sorry, but waiters and waitresses don't count) that has been fired because of the enforcement of a dress-code policy, so I have to question the merits of explicitly stating one.

Look at truly innovative technology companies and you will notice one thing lacking: a dress-code policy.

## Software IT

Software engineers, that are good, are tinkerers. We have broken more then a few computers in our day, and almost always figure out why and fix it. The job of an IT department is to prevent employees from tinkering with computers, because it costs the company valuable effort.

These two departments can only co-exist as peers. In general if IT provides API to standard services like Email then software developers will never have to bother IT with questions. After all software developers are usually overqualified IT.

If the company codes for the Linux platform, but software developers are required to use windows machines, because that is what IT can support, this is a sign of an imbalance between Software and IT.

## No SVC

Every programmer that has been out of college for more then a semester knows about Source Versioning Control systems. There isn't even a debate anymore, they are essential for programming. A company without at least some type of SVC is scary.

If you know and understand {{% wl Git %}} then you can solve this problem for the company, but if the other engineers are not familiar with such system there is going to be strong, and often emotional, opposition. Not something a professional should have to deal with.

## Commercial SVC

There is no commercial SVC software out there that has the usefulness that Git does. There are a lot that fill in for the lack of usefulness by adding bloat, like IP protection. Commercial SVCs are always sold to detached CTOs by sales guys that hide its destructive nature.

Only a detached CTO would buy software without first letting the developers review it for usefulness. I do honestly think commercial SVC systems are destructive because they always designed for an audience that is not software developers. At best this means that the developers adapt, but usually it means that adding wildly complicated procedures to deal with the lack of a good flow.

VSS is a great example of this failure. It only supports file locking, because it is easiest to implement. It also could not deal with merge conflicts, so external tools has to be purchased to deal with that. Also, if files were locked the nightly internal backup could not run or it would create a corrupt backup. So you couldn't keep files locked overnight. It didn't support branches (as we know them today) so everyone worked on the same set of files, and locked each other out all the time. It was hell!

## No CI

This is the first thing I do before any code is written. I create an empty repo, put an a rake/make/cake file that simply has one step "ci" and attach that to a CI server. As soon as we know the details of the language, testing framework, coverage metrics, etc... I adjust "make ci" to do those things.

It is so simple to setup that if it isn't there then it erodes my confidence in the entire project. Tests are the only reliable communicator of assumptions, and not having a system that actively enforces those assumptions will cause greater complications later.

## Required IDE

Detached management love IDE's, because they speak in a language that managers understand: GUI. Sometime they are useful and sometimes they are not. And most of the time they bloated, slow, and expensive.

Any editor that can shell out is an IDE. So if using a specific IDE is required then someone is forcing their bad ideas on you. The emacs vs. vi debate still rages because they are as powerful (in cases more so) then what we think of as IDEs (xcode, eclipse, etc...), but they both are and neither requires a specific "project" file to manage a project.

## Cowboys and "Heroes"

Cowboy coders prefer to work alone, often thinking themselves and their code superior to other developers. If there are not code reviews, it is usually because of adamant opposition from these guys. Even if they lose the code review fight they will fight be exempt from code reviews themselves.

All they do is hack some stuff together without thought of quality or maintainability and call it done. They are dangerous, and the quality of the system will suffer as the project gets too complicated to fit entirely within their own heads.

A "hero" is a very loud cowboy. They are the software equivalent of "yes" men. They tell management what they want to hear, and often gain position greater then their experience and expertise. Unfortunately they almost always spell doom to a project in one way or another. Sometimes it is outright fail to produce a workable product, and sometimes it is a mass exodus of skilled workers.

Both cowboys and "heroes" have a habit of getting entrenched and are very hard to unseat, but the project will not survive them.

## Coding Silos

For reason beyond my understanding managers usually frown upon agile approaches like pair programming. It is seen as wasting company time and tantamount to theft. Instead they would prefer programmers to "just do their job" which involves writing code and not much else.

A vertical silo is where you are expected to do everything from the GUI to the database layer. On small projects this is expected and even wanted. But rarely (unless you doing it on your own time) will a progressional project be that small. When a person holds the entire stack in their heads then the apparent usefulness of MVC (or similar patterns) breaks down. This later leads to scaling problems.

A horizontal silo is when there are many projects for the company and you maintain the same role on ALL of them. A major problem is in solving the wrong problems. For example: you are the DBA for all apps in the company. You have a very expensive Oracle DB and know it well, and have a bunch of homegrown management scripts. Therefore all web apps run on the same Oracle DB server because it is quicker and easier for you, and now there are two single points of failure (you and DB). Sqlite would have been good enough, but that isn't how specialized people think.

> When all you have a hammer all problems look like nails - Barry Gruenberg.

Another problem with horizontal silos is a stagnating. For example: a junior engineer wants to use a new distributed key/value store like Cassandra or CouchDB. You argue with management that a simple key/value table in the already sharded Oracle DB would be good enough and would save the company money in both hardware and effort. You might be right, or you might be wrong; but you are guaranteed not be to exposed to a different way of thinking. In the long run that simple act adds complacency and stagnation into large companies.

The only sustainable solution is a cross functional team, where everyone has areas of strength and weakness but they work on the system as a whole.

## Value Based Estimates

At market driven company it is not uncommon to see estimates done by those not qualified to do them (management). A marketing department will usually attach a proposed value of a given feature, or product. This automatically skews the estimate by placing an upper bound (the value minus require profit).

If the company communicates well then realistic estimates are given by developers, and if those estimates are higher then the projected value then the feature or product is not invested in. In marketing driven the realistic estimate are not done or are ignored and the project moves forward with the value estimate. This then adds instant legacy as the correct implementation was not worth the effort, so a half-assed job was done instead.

Hopefully, the team at least invested in a means to fix past mistakes. But sometimes that isn't a feature worth the effort.

## Detached Management

Much of what has already been stated come from the same source: detached management. A detached manager will often blame the developers for failures in software and procedures he/she is forcing on them. "A carpenter doesn't blame his tools" is a common excuse. If a developer is lazy and has no interest in keeping up with the industry it is a valid excuse, but more often the manager just doesn't want to hear that they did not fully think through the problem before forcing a solution.

Early in the game this looks like a manager that doesn't show up to scrum calls because they are too busy.

## Overstaffing

One of the easiest ways to make a budget look needed is to hire a bunch of staff. If there is an influx of new hires, especially if they appear unqualified or under qualified then it is possibly for budgetary reasons.

The unfortunate side effect of overstaffing (even if the staff is qualified) is laziness. More staff equals more cooks in the same amount of space, which in turn equals more confusion and less efficiency. This lack of efficiency leads to an imbalance of responsibilities and therefore some will be overworked and other underworked. Underworked employees become complacent, and overworked ones become annoyed and will work less. This drives overall productivity down.

Adding staff at any stage of a project makes the project take longer and that will continue to be true until we learn to download and upload expertise.

## Market Driven or Marketing Driven company

Companies driven by a Marketing Department (however good) are reactive companies. There is no vision of how things should be, or why they should be that way. It takes a visionary to reduce a companies offering, and instead focus on quality. Marketing departments do not do this, they always add more.

In fact, there is a certain critical mass in which a marketing department exists to exist. This is the point at which the marketing budget becomes as big (or bigger) then the R&D and Engineering departments, so they can convince users of the usefulness of the product (which probably isn't).

## "Putting out fires"

Anytime I hear "putting out fires" I know the project is doomed. Things probably got this way gradually over time, but at this point there is too much technical debt to warrant moving forward. Projects that cannot move forward die.

The only way to prevent this situation is to head it off early by dealing with heroes before they cause trouble and keeping marketing in check.

## "Continuous Work"

Anytime I hear someone from a company (usually marketing) mention continuous or unending work I get nervous. I understand that it is an attempt to make it seem like the job is on going and therefore safe, but I am not a factory worker. The stuff I work on should have a natural conclusion, and the knowledge I gained should then be used on another project.

## "Competitive Salary"

Anytime I hear "Competitive Salary" I know three things:

1. it is a lie, and by extension the company lies.
2. they gear to recruiters, not people being hired
3. they under value employees and will undervalue you

Huge red flags are raised.

## Agile Lip-service

A lot of companies are flocking to Agile as an end all be all. But that is exactly what Agile is not. I have detailed in [Problems with Agile Implementation]( {{< ref "20110110-problems-with-agile-implementation" >}}) a number of bad implementation and companies that think Agile is a silver bullet are likely to make some or all of them.
