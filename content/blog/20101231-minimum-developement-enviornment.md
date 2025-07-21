---
title: 'Minimum Developement Enviornment'
date: 2010-12-31
lastmod: 2010-12-31

# Keywords help in classifying content
keywords:
  - Minimum Developement Enviornment
  - Development
  - Programming
  - CI
  - CD
  - GIT
  - IDE
---

Every developer has their own opinions on what tools are needed. This is a very malleable list, in general, but in my ten years of experience I have found some key things are are needed. Sure, you can live without a lot of these, but they will make your life easier.

<!--more-->

## Text Editor

A text editor is where a programmer is going to spend most of their time. I am sure it is nice to have all the IDE features right there in the side bar or right click menu, but a lot of IDEs (Eclipse I am looking at you) add this fluff at the expense of a truly useable text editor. I don't need my editor to take 15minutes to open if all I am going to do is edit a single file. I don't need a plugin architecture if all I want to do is edit a script and run it from the editor.

I use TextMate right now because it has all the features I require. If another editor comes along (one that is updated regularly) that has them then I will switch.

### Gutter

It isn't enough to have a note somewhere about the current line (for example the bottom). I want a gutter that takes up constant room and shows the line number as well as other things like: cursor location, folding marks, breakpoint/quick jump points.

### Syntax Highlighting

This is a must! Sorry vi. It is a very quick way of determining if the syntax is correct. It also make the code easier to read.

### White space highlighting

Very often tabs are mixed with spaces. This is a no no, and if you are working with me I will not accept mixed code. Use one or the other, not both interchangeably. And have an editor that can show you the difference. If it is a feature that vi has then you better be damn sure your editor has it as well.

### Vertical Selection

There are times where vertical selection comes in handy. Basically it places the cursor as a box and anything you type is repeated once for every line. Great if you need to add indentation to the front of a lot of lines at once.

### Folding

When programers write 1400 line functions (don't scoff you know you have done it) it is nice to hide those. Basically any block that is not immediately useful to me is hidden.

### Hotkeys (for everything!)

The Windows method of pressing alt+X, where X is the underlined letter of the menu, is not what I mean. Everything should have a single hotkey combination what does exactly what I want. For example to run the current file as a script `cmd+R` seems reasonable to me. It also has to be single press. Sorry Emac `ctrl+x,ctrl+r` just to run a file isn't going to cut it.

### Mouse Support

Yep, selection especially vertical selection is just faster with a mouse.

### Quick Search

`cmd+f` should present a search box. `cmd+g` should quick search for what was already typed in the search box. And the search box should be erased when opening a new file. `shift+cmd+g` should search up instead of down. All search should automatically wrap without asking or prompting. I can see from the scroll bar that a wrap happened.

### Search and Replace

Search has to support regex, with matching. Replace needs to support matched items (usually $N where n is the paranes set). Replace should allow replacing in the entire file, or just in the highlighted section.

### Quick Open

When opening a directory to do not all files open in the editor. I just want a file browser and a place where the text files will open. Quick open (`cmd+t` in TextMate) should show a dialog listing all the files that meet my typing so that I can quickly open the one I want. I do not want to have to type a full path, or search for the file. The editor should index the file names so that I can quickly open them when I want. Updating of the list of files also has to happen live.

### Indent Correction

Contributors will mix tabs and spaces because they will not enable white space highlighting. If the code is already checked in and I have to deal with it then I am going to have my editor re-indent the way I want. I will commit this first then start making changes. What way my changes can actually be seen and are not hidden in indentation hell.

### Scripting Support

Any editor that can run scripts is an IDE. In many case they are better because you get a great editor first, and an ability to extend it. Most IDE spend a lot of time outthinking you as the user. More specifically they spend a lot of CPU and memory on things in hopes that they might be useful to you one day. This is CPU and memory that could be used by your kernel to do other things that are actually useful to you.

### Command line tool

I spend a lot of time at the command line. So I really need to be able to open a file in the current directory (or the directory itself) from there.

### Control Comments

These are comments that can be placed at the top of a file to control how the editor shows the document. They are normally hidden within comment blocks so do not affect the flow of the document, but are very useful for controlling file specific changes.

### Terminal

The reverse is similarly true. Sometimes you need to run a command without leaving the editor. It is best is the editor can do that via a real terminal.

### Native/Quick start/Low Memory

Java apps might work on a lot of different architectures, but they are dog slow and memory hogs. The editor I use is going to be the editor I use for almost all text work. I might open a lot of files at once, or I might open only a single file at a time. It needs to be fast.

## Version Control

I use git. You will eventually use it as well so you might as well learn it.

- Non-locking Commits
- Distributed
- Network Fast
- Personal Branches
- Tags

### Merging

SVN's merging was a joke. It was so bad that it made you do all the work, so you basically never did it. I have yet to have serious problem with GIT merging and I use it daily. In fact I might have 2 to 3 active branches going at one time, and I will randomly merge between them. It just works. I don't know why, nor do I care. And when it fails, it does so clearly. It doesn't just puke random output at you.

## Misc

The following more important when you start working in a group setting. At work they will often be given to you or forced upon you, but for personal projects I recommend having a set of free or OSS options to pull from.

### Cloud Repository Storage

This can be anything that gets the code off of your machine. It is the means of sharing code between other people and machines. The requirements are minimal, but basically it has to support the SVC tool you use (usually git), allow for both human and machine accounts, and have a permissions model to allow basic limiting of access (for example, machines get read-only access).

### Wiki

Some location will be needed so that you can get your ideas out of your head and into someone else's; be it the user of your software or another maintainer (like the future you). It doesn't have to be anything complex, and the concept of wiki style documentation is about as light weight as you can get. Have one.

### Requirements and Issue Management System / Service

Once your software is used, especially if used by others, things will come up. Since no one can spend every moment of every day just implementing you will need a place to park requests so that you can focus on other things. This is where a "ticketing" system comes in.

The basic requirement is a system that can house multiple tickets. Each ticket needs a text box where you can describe what the issue is or what needs to be done, the ability to assign it to someone, the ability to order the ticket, the ability to comment or discuss, and finally the ability to track status (open, done, etc...).

Caution: Many of the systems readily available were built in a time of code bloat, where the belief was that the code needed to handle all things. This has lead many of the systems out there to be a basic copy of someone else's complex workflow; codified. This can lead to bloated and inflexible process, so unless you really need the bells and whistles I'd avoid them in favor of something really light weight. Sometimes a spreadsheet is good enough.

### Testing Framework(s)

Regardless of what you are building you will need to test it to make sure your change didn't break something that was already working. I could write entire blog entries on proper testing techniques, but the basics are the need for three types of testing system.

1. Unit test - These tests - always written by programmers - test the very low level objects. Usually they focus on edge cases in the logic. Often times a programming language will have this built in.
2. Behavioral tests - These tests - also always written by a programmer - prove that the work is complete. In other words these prove the "behavior" of the feature being coded and are often extracted from the requirement of the feature itself. The Frameworks you choose will determine the Behavioral test frameworks that you have available to you and the form those tests take. None is really better then another as long as in 2 to 5 years you can re-read the tests to determine if the described intent matches the logic. If it is difficult to marry those two things then choose a simpler test framework. Just remember [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) is not a thing in testing.
3. System tests - These tests - written by QA - prove the software works outside of itself. That is that they test the final artifact that is produced. They are always **outside** the repo itself and always on the built artifact. These tests are often paired or versioned with the artifact, so that you can go back and retest old software to determine if an issue exists there or not.
    1. For a library this might be using it downstream project, so the downstream's unit tests act as system tests for the upstreams.
    2. For a binary this might be coping the binary onto a host machine and executing it.
    3. For an appliance this might be booting it, and using its API.

Notice how integration test is missing from the above? That is because it is an overly board and over used term. As such it often comes to mean "test what is easy to test", and thus becomes an ultimate waste of time. The above testing styles have a clear intent, and intent is everything. So put on different hats and test correctly instead of what is easy.

### Continuous Integration Service / System

Once the tests are written, and the compile and packaging details ironed out, there should be a system that isn't the developer to does that. Ideally this system can be built from a minimal config using a set of directives that are defined in configuration files stored with the code itself. This ensures that the config is versioned along with the source code (i.e., Infrastructure as Code). Also, it ensure that a single system can be used for multiple projects thus dividing the maintenance costs across projects.

What the CI server / service should do is:

1. Monitor for change to the code
2. If changed, it
    1. downloads the new code
    2. finds and blindly executes the IaC file
    3. reports pass / failure status

Caution: It sounds simple enough, but finding the right balance of expressive IaC that runs fast enough that isn't hard to rebuild when it is a corrupted is extremely difficult. As the build system gets more complex and more scripts are written to work around its problem the Ikea effect can kick in making the build machine seem more valuable than it really is. Don't invest highly in an "CI ecosystem" (i.e., Jenkins), instead treat it as a set of fungible runners executing build and test scripts that are versioned with the source it builds. Be able to delete and rebuild the CI platform quickly, so that when a better CI platform come along you are in a position to switch quickly.

### Artifact Store

Whatever you are building you should not use the source repo itself as the final state. Instead you should CI it (test, build, and package) the software and then capture the package somewhere else.

What and how you do that will depend on what language you use, and how downstream user need to consume the artifact. In some cases your code might need to built into multiple artifacts stored separately.

The only real advise is that the Artifact Store has to handle the distribution of the artifacts, which means it need to be able to hold multiple versions and have a permissions model that allows write access by the build process and read-only to downstream consumers. Also, it needs to be able to handle the amount of parallel downloads of the artifacts.

### Continuous Deployment Service / System

If you are building a library or artifact then you won't need one of these. Testing, building and coping the artifact to a final storage location is going to be enough. However, if you are hosting a service then you will need to have an automated means to make the new software available customers automatically.

There are many styles of deployment and no one tool that is good at them all. Also, the CD platform you can use will be determined by how you run your service.

Basically, it needs to be able to:

1. Check for the need to deploy
    1. Usually either checking for new versions of artifacts, or via manual push button. Anything else can rolled up into one of these two options.
2. Delta the current to expected state and determine the correct commands to run
    1. Gone are the days when you write a script to deploy. Modern CD is declarative.
3. Recover from issues in the deployment
    1. Again, declarative. You say how something can recover on error and CD figure out if it is needed and what the actual steps would be. Could be a retry, a roll back, a halt, or something else.
4. Notify a human

Caution: CD can be "implemented" using a CI platform but that is fraught with problems. It is tantamount to using a hammer on screws. Yes you can, but should you? No you shouldn't. Pick a tool that is aimed at the end goal of the deployment and makes part easy.
