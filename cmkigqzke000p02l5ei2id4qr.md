---
title: "Understanding Git: Why It Exists and How We Use It"
seoTitle: "Git Basics: Purpose and Usage Explained"
seoDescription: "Git: a decentralized version control system, ideal for collaboration and offline work. Learn its evolution and features for efficient coding"
datePublished: Fri Jan 16 2026 18:30:00 GMT+0000 (Coordinated Universal Time)
cuid: cmkigqzke000p02l5ei2id4qr
slug: understanding-git-why-it-exists-and-how-we-use-it
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1768663680031/964603bc-8940-4c7c-91a2-18f7f053fab8.png
tags: software-development, version-control, git, beginners, developer-tools, git-commands, git-basics, chaicode

---

## What is Git

Git is a type of **Version Control System (VCS)**.  
It is **open source** and runs on your **local machine**.

Before diving into Git, it helps to understand **why version control exists in the first place**. We discussed the idea of VCS in an earlier article.  
Give it a read: [**Why Version Control Exists: The Pendrive Story Every Developer Has Lived**](https://dhruvbhartia07.hashnode.dev/why-version-control-exists-the-pendrive-story-every-developer-has-lived?showSharer=true)

To understand Git better, let’s first look at how version control evolved over time.

---

### Early Ways of Managing Code (Before Git)

#### Method 1: Local Versioning

A very common early approach was to maintain multiple copies of the same project locally:

```plaintext
project_1  
project_2  
project_3  
project_final  
project_final_2
```

or sometimes using timestamps.

This approach:

* Quickly becomes messy
    
* Leads to confusion over which version is correct
    
* Allows only **one person** to work comfortably
    
* Lives entirely on a personal device
    

There is some sense of versioning here, but no real tracking or collaboration.

---

#### Method 2: Centralized Version Control (CVCS - e.g., SVN)

A better approach was to introduce a **central server**.

* The server stores project files along with their history
    
* Developers fetch a copy, make changes, and push them back
    
* The server manages the code and its history
    

This solved collaboration issues but introduced new problems:

* You always need connectivity to the server
    
* If the central server fails, the project history is at risk
    

---

#### Method 3: Decentralized Version Control (DVCS)

The centralized approach still had limitations.

A decentralized approach solves this by:

* Keeping the **entire history on every developer’s machine**
    
* Allowing work to happen **offline**
    
* Enabling sync with any peer, remote, or server at any time
    
* Removing a single point of data loss
    

**Git follows this decentralized approach.**

Every developer has:

* The full code
    
* The full history
    
* Full tracking information
    

Git runs locally, while platforms like **GitHub, GitLab, and Bitbucket** are **hosting services built on top of Git**.

One interesting design choice in Git is that it **does not store file diffs**.  
Instead, Git stores **snapshots of the repository at a point in time**.  
Each commit becomes a reference to the state of the entire repository at that moment.

> If you are interested more in this, I have linked an article explaining git internals at the end of this article.

---

## Why Git is Used

Before version control systems existed, managing projects was error-prone and difficult.

When VCS was introduced, it helped - but early implementations came with their own limitations.

The evolution roughly looks like this:

* Projects shared using pendrives, emails, or zip files
    
* The idea of version control introduced
    
* Multiple implementations appeared:
    
    * **Local VCS**
        
        * Tracking exists
            
        * No collaboration
            
        * Everything stays on one machine
            
    * **Centralized VCS**
        
        * Easy collaboration
            
        * Requires constant server access
            
        * Risk if the server goes down
            
    * **Decentralized VCS (Git)**
        
        * Full local history
            
        * Offline work
            
        * Independent collaboration
            
        * No single point of failure
            

Git became popular because it **solved the limitations of both local and centralized systems** while keeping collaboration fast and reliable.

---

## Git Basics and Core Terminologies

Below are some common Git terms you’ll frequently come across.

### Repository (Repo)

A repository is: `Project files + .git directory`

The `.git` directory is where Git stores all tracking and history information.

---

### Working Directory

The **working directory** is your actual workspace:

* Where you see files
    
* Where you edit files
    
* Where changes are made before being tracked
    

---

### Commit

A **commit** represents:

* A snapshot of the code at a given time
    
* A unique hash
    
* A commit message
    

A chain of commits forms a **linked timeline of the project’s history**.

---

### Staging Area

The **staging area** is a special cache-like area that sits between: `Working Directory → Repository`

It allows you to:

* Select specific changes
    
* Decide what should be included in the next commit
    

---

### Branch

A branch is **a pointer to a commit**.

Using branches allows:

* Parallel work
    
* Independent experimentation
    
* Multiple lines of development alongside the original
    

---

### HEAD

`HEAD` is a reference to:

* The current branch
    
* The current commit
    

In simple terms, it tells Git **where you are right now**.

---

### Remote

A remote is **another copy of the repository**, usually hosted on a server such as GitHub or GitLab.

---

## Common Git Commands

Below are some commonly used Git commands grouped by purpose.

---

### Starting & Inspecting

**Initialize a repository**

```bash
git init
```

Creates a new `.git/` directory.

---

**Check repository status**

```bash
git status
```

Shows:

* Changed files
    
* Staged files
    
* Untracked files
    

---

**View commit history**

```bash
git log
```

---

### Making Changes

**Stage a specific file**

```bash
git add <filename>
```

---

**Stage all changes**

```bash
git add .
```

---

**Create a commit**

```bash
git commit -m "message"
```

Creates a snapshot from the staged changes.

---

### Branching

**List branches**

```bash
git branch
```

---

**Create a new branch**

```bash
git branch <branch-name>
```

---

**Switch branches**

```bash
git checkout <branch-name>
```

---

### Fixing Mistakes

**Discard local changes for a file**

```bash
git restore <filename>
```

---

**Undo last commit but keep changes staged**

```bash
git reset --soft HEAD~1
```

---

**Undo last commit and discard changes**

```bash
git reset --hard HEAD~1
```

---

> Below is the article in which we go through practical example to understand git internals, give it a read:
> 
> [**How Git Works Internally: Building a Mental Model**](https://dhruvbhartia07.hashnode.dev/how-git-works-internally-building-a-mental-model)