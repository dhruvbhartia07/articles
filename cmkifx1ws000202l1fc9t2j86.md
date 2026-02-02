---
title: "Why Version Control Exists: The Pendrive Story Every Developer Has Lived"
seoTitle: "The Evolution of Version Control Systems"
seoDescription: "Learn how Git addresses coding challenges, illustrating the importance of version control systems"
datePublished: Fri Jan 16 2026 18:30:00 GMT+0000 (Coordinated Universal Time)
cuid: cmkifx1ws000202l1fc9t2j86
slug: why-version-control-exists-the-pendrive-story-every-developer-has-lived
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1768661898397/a2a10ca8-9844-49f0-b665-4336a93a4760.png
tags: software-development, programming, version-control, git, vcs, learninginpublic, version-control-systems, techlearning, developer-mindset, sourcecontrol

---

## General Mindset: Asking *Why* Before Using Any Tool

Before jumping into any new tool or technology, I like to pause and ask a few basic questions:

* Why do I need this tool?
    
* Why does this exist?
    
* What problem does it actually solve?
    
* Can I work without it?
    

This article is written with the same mindset.

It is **not** an explanation of Git or how Git works internally.  
Instead, it is an attempt to understand **why version control systems exist in the first place**, and what problems they were designed to solve.

---

## Life Before Version Control Systems

Before version control systems became mainstream, developers still built software, collaborated in teams, and shipped projects. But the way collaboration happened was very different.

Code was commonly shared using:

* Pendrives
    
* Emails with ZIP attachments
    
* Shared folders
    
* Files and directories named like:
    
    * `final`
        
    * `final_v2`
        
    * `latest_final`
        
    * `final_latest_really`
        

At a small scale, this *seems* manageable.  
But as soon as more than one person starts working in parallel, things begin to break in subtle ways.

To understand this better, let’s look at a simple story.

---

## The Pendrive Story: Three Friends, One Project

### The Setup

Three friends - **Alice, Bob, and Charlie** - are in college and decide to build a personal profile website together.  
They do not know about any version control system.

The application has three components:

* Navbar
    
* Profile section
    
* Blogs section
    

They divide the work as follows:

* Alice works on the **profile**
    
* Bob works on the **blogs page**
    
* Charlie takes the **navbar and index page**
    

Charlie finishes early. He copies the code to a pendrive and passes it to Alice.  
Alice copies it to her local system and then passes the pendrive to Bob.

At this point, Alice and Bob are working independently on their assigned features.

---

### Where Things Start Breaking

While Alice and Bob are working, Charlie becomes free and decides to improve the navbar styling.  
He asks Bob for the pendrive.

At the same time:

* Bob finishes his blogs page and adds it to the pendrive
    
* Charlie copies his updated navbar to the pendrive
    

Curious to see how things look together, Charlie runs the code with the navbar and blogs page.  
He notices some bugs and misalignments in the blogs page and does a quick fix.

Meanwhile, Bob also finds a few issues in the blogs page and fixes them on his system.

Bob asks for the pendrive back.  
Charlie passes it to him, along with a note explaining the changes he made in the blogs page.

Now Bob is stuck.

He can’t simply replace his entire blogs folder anymore.  
Some issues are already fixed by Charlie, while others conflict with Bob’s own logic.

To deal with this, Bob creates a new folder called `_latest`, compares both versions, and manually reuses parts of the code.

---

### Silent Overwrites and Lost Changes

During all this, Alice finishes her work and asks for the pendrive.

Bob passes it to her.  
Alice copies her profile code to the pendrive.

While reviewing the code, Alice notices a small typo in the index page and fixes it.

Later, Bob completes his remaining fixes and asks for the pendrive again so they can finalize the project.

Alice shares the pendrive.  
Bob replaces all the files on the pendrive with the code from his `_latest` folder, assuming Alice’s work would not be impacted.

When all three check the final code, Alice notices something surprising:  
the typo she fixed in the index page is gone.

After discussion, Bob realizes he unintentionally overwrote Alice’s fix.  
Alice had forgotten to leave a note about the index page change, and Bob had no way of knowing it existed.

The fix was silently lost.

---

## What This Story Shows Us

Even for a **very small project**, collaboration became difficult.

Problems that appeared:

* Code getting overwritten without anyone realizing
    
* Changes getting lost silently
    
* Manual notes becoming a dependency
    
* Folder comparisons like `_latest` becoming normal
    
* No reliable history of who changed what and when
    

Everyone tried to be careful.  
Still, things broke.

---

## Why This Completely Fails at Scale

As teams grow, this approach becomes impossible to sustain.

One option is to enforce strict discipline:

* Always leave notes
    
* Always communicate every change
    
* Be extra careful while copying files
    

Another option is to treat the pendrive as the only editable source:

* If you have it, you can make changes
    
* If you don’t, you wait
    

This can be replaced by a server where only one person edits at a time.

While this sounds safe, it comes with heavy constraints:

* No real parallel work
    
* Long waiting times
    
* False sense of safety
    

Even systems that allow multiple people to edit at the same time show how difficult it is to get things right in a single attempt.

This is where the illusion of **parallelism vs concurrency** becomes clear.

There is a gap - and manual coordination is not enough to fill it.

---

## The Idea That Changes Everything

Charlie recognizes this gap and comes up with an idea:  
an automated tracker called **Charlie Code Tracker (CCT)**.

CCT does a few important things:

* Tracks what changed and who made the change
    
* Can be installed on each developer’s local machine
    
* Allows everyone to work freely on their own system
    
* Helps highlight inconsistencies or overlaps during sync
    
* Allows pulling others’ changes and pushing your own
    

Because changes are tracked automatically, developers no longer need to rely on memory or notes.

This idea removes the restriction of working on a single device and enables safe collaboration.

---

## This Is Why Version Control Exists

This **CCT idea** represents what a **version control system** is meant to solve.

Version control systems exist to:

* Enable parallel work without overwriting
    
* Maintain a reliable history of changes
    
* Make collaboration safe, traceable, and scalable
    
* Reduce human error instead of relying on discipline alone
    

Teams may choose to treat a shared server as a coordination point, but the core value lies in **tracking history and changes**, not just storing files.

---

To understand how Git handles tracking and history internally, the next article will focus on:

> **Give it a Read:** [**How Git Works Internally: Building a Mental Model**](https://dhruvbhartia07.hashnode.dev/how-git-works-internally-building-a-mental-model?showSharer=true)