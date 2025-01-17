# Git

This note is based on Ray Ma's Lecture 06 Git, supplemented by [Git](https://git-scm.com/doc), aiming to help students master git to collaborate with others on code projects.

## Table of Contents
- [0. Introduction](#0-introduction)
- [1. Why Use Version Control](#1-why-use-version-control)
- [2. Centralized & Distributed Version Control](#2-centralized--distributed-version-control)
- [3. Git and GitHub](#3-git-and-github)
- [4. How to Set Up Git and Basic Commands](#4-how-to-set-up-git-and-basic-commands)
- [5. Branch and Merge](#5-branch-and-merge)
- [6. Remote Collaboration](#6-remote-collaboration)


## 0. Introduction

![Linus Torvalds](https://avatars.githubusercontent.com/u/1024025?v=4)

Linus Torvalds (Github: [torvalds](https://github.com/torvalds)), the creator of Linux, said:
> Talk is cheap. Show me the code.  

So he created Git in 2005 out of necessity and frustration with the existing version control system, after a licensing dispute caused the Linux kernel project to stop using their existing version control system, BitKeeper. Here's the full context:

1. The BitKeeper Issue

The Linux kernel development team had been using BitKeeper, a proprietary distributed version control system. BitKeeper allowed developers to collaborate efficiently, but in 2005, the free use of BitKeeper for open-source projects was revoked due to disagreements between its developer, Larry McVoy, and the open-source community.

2. The Need for a Replacement

With the loss of BitKeeper, the Linux community urgently needed a new system to manage the vast and complex development of the Linux kernel. Linus decided to create his own version control system to meet the specific needs of the kernel developers.

3. Torvalds' Goals for Git

Linus had several key goals in mind when designing Git:
• Speed: Git needed to handle the large-scale development of the Linux kernel quickly.
• Distributed Development: Developers needed the ability to work independently and merge changes later.
• Data Integrity: Ensuring that the history of the project was secure and changes were traceable.
• Scalability: Git needed to handle the massive size and activity of the Linux kernel repository.
• Simple Design: Linus wanted Git to focus on the core functionality needed for kernel development, leaving less critical features for later.

4. Rapid Development

Linus wrote the initial version of Git in about two weeks, releasing it as free and open-source software under the GNU General Public License (GPL). It quickly became popular, not only for Linux kernel development but also for other open-source projects.
Since its creation, Git has evolved and gained widespread adoption in the software industry, becoming the de facto standard for version control. It is now maintained by a large community of developers, though Linus was instrumental in its design and initial

## 1. Why Use Version Control

1. History and traceback
2. Collaboration
3. Backup and Recovery
4. Undo Changes or traceback the old version
5. Branch and Merge
6. Version Tracking
7. Experiment New Features with Branches without affecting the main code

## 2. Centralised & Distributed Version Control


![git_central_and_distributed](./assets/images/git_central_and_distributed.png)




### 2.1 Centralised Version Control  (Subversion) 集中式

Working repository will be stored in central repository. People who only have access to the central repository can download and work on the code. It means they have to go to the place where the central server (central repository) is so they can work on the code. In other words, they have to work on the code in the same place. aka the company office (server). 

Since they can't work on the code without physically being in the server or intranet, they have to update and commit the code to the central repository. 

This origins from the traditional software development company, where source code is not open source, and stored in the central repository. People who only have access to the central repository can download and work on the code. It means they have to go to the place where the central server (central repository) is so they can work on the code. In other words, they have to work on the code in the same place. aka the company office (server). 
 

 Centralised version control system provides various version control functions:
 - Log: provides history
 - Merge: file merge
 - Revert: version rollback
 - Branch: version branch

> In my school 42London, we use centralized version control system. It means that we have to be in the compuse to work on our code and push it to the central repository. 

### 2.2 Distributed Version Control (git为代表)
Distributed version control system is the opposite of centralised version control system. It means that each developer has their own local repository, and they can work on the code locally. They can also push their code to the remote repository.

They don't have to be in the same place to work on the code. They can work on the code in different places.

In a open souce project, there is no central repository, so there is a remote repository. In local, there is a local repository, which is not a working copy, but a complete repository. Through `pull`/`fetch`, we can get the complete file of the remote repository, including the complete log; through `push`, we can submit the modified file.

- Distributed version control: there is no centralised server, and the local repository is a complete repository.
- Now, many corporates started to manage their projects using distribution version control system and slowly migrate their projects to remote repository like Github or Bitbucket.

## 3. Git 和 GitHub
GitHub provides a third-party free and open-source hosting platform for developers. It can be used for: review, discussion, pull request, publish project.
- Github is a platform for free to use but it doesn't mean completely free 
  - Free for small businesses (Any open source software), open source projects, personal use 
  - Charge for private , enterprise，integration (CI/CD)
  - Repository owner has management rights; each participant will have a local repository, and a sync relationship with the remote repository (downloaded and pushed up)


> Note
> As a professional IT, in actual work, you use the company's computer, don't install anything on the company's computer, it's not professional.
> Don't upgrade the company's software at will, please read the documentation and policy to check which version of software is allowed to be used, if you can upgrade software, usually there will be an IT department for you to consult before you taking any action. In any case, it will cause compatibility version problems, so don't upgrade any software.


- Through GitHub web interface:
1. Go to repository Settings
2. Select "Manage access"
3. Click "Add people" or "Add teams"
4. Set permission level to "Write" for basic push/pull access

For most collaborative projects:

Regular team members usually get Write access
External contributors usually get Read access (they can fork and submit PRs)
Team leads might get Maintain access
Project owners/managers get Admin access


Here's a clear comparison of Git permission levels in a markdown table:

| Permission Level | Key Capabilities | Common Use Case |
|-----------------|------------------|-----------------|
| Read | • View and clone repository<br>• Create issues<br>• Submit pull requests from forks<br>• Download releases | External contributors, stakeholders who only need to view code |
| Triage | • All Read permissions<br>• Manage issues and PRs<br>• Apply labels and milestones<br>• Cannot write code | Project managers, QA team members who manage issues but don't code |
| Write | • All Triage permissions<br>• Push to non-protected branches<br>• Create/delete branches<br>• Create/manage releases<br>• Merge pull requests | Regular team members, active developers |
| Maintain | • All Write permissions<br>• Manage PR merging<br>• Modify protected branches<br>• Cannot change settings<br>• Cannot delete repository | Team leads, senior developers |
| Admin | • All Maintain permissions<br>• Change repository settings<br>• Delete repository<br>• Add/remove collaborators<br>• Set up webhooks/integrations<br>• Transfer ownership | Repository owners, project administrators |


Github additional features:
- Github Copilot is a AI coding assistant developed by GitHub and OpenAI, it needs to be paid.
- Advanced Security: static scan, dynamic analysis, vulnerability scanning, etc.
- Actions: can do CI/CD pipeline
> Git is a CLI(Command Line Interface) tool.
> - But Git also has various GUI tools, also called Graphical User Interface. It's not necessary, vscode can install GUI plugins.

## 4. How to set up Git and basic commands
Install Git:
You can download it from https://git-scm.com/

Or using command line interface to download git:

For Macos

```
# Install Homebrew first (if not installed)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Git
brew install git

# Verify installation
git --version
```

For other systems, you can Google it or ask ChatGPT.

How to check if Git is installed:
```
git --version
```

> It's not necessary to install the latest version, just keep the latest major version, the first two digits are the same.

### 4.1 Basic Git Setup  
- Global Setup  
  - `git config --gobal user.name "<Full Name>"`   - Deveoper's Real Name
  - `git config --gobal user.email "<email>"`  
    - Use company email in work
    - Use GitHub registered email in personal project
  - `git config --gobal color.ui auto` Sets up automatic colorization of Git command output. Makes Git's output more readable by adding colors to different types of information. Example: Different colors for added, modified, and deleted files in git status 
  - `git config --gobal merge.conflictstyle diff3`  
    - Changes how Git displays merge conflicts.
    - Shows three versions during a conflict: Your changes, the originak text, their changes
  - `git config --gobal core.editor "code --wait"`  
    - Sets Visual Studio Code as your default Git editor
    - The `--wait` flag tells Git to wait until you close the file in VS Code
    - Used when writing commit messages or resolving merge conflicts
    - If you use a different editor, you would replace "code" with your editor's command

  `code .` in command line interface is telling the terminal to launch VSCode under the current directory 
  - `git config --list --global` to check the config list


- Git default uses global setup

![](https://i.imgur.com/llSjTBg.png)

- Local Project Setup
  - When config without --global, it's project setup
  - project local setup has higher priority than global setup. Which means if you have preset the config globally like you are using company email, but you are working on a project, you can use your personal email in the project local setup.

  ![](https://i.imgur.com/TgurCOH.png)
  
> If the code command doesn't work on MacOS, you can refer to this: https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line

### 4.2 Git Workflow
![](https://i.imgur.com/NzpiH4B.png)


### 4.3 Create Local Repository  
Using command line interface:

- First you need to `cd` to the directory you want to create the repository.
- Second, you need to use `git init` to create the repository. After you run this command, you will see a `.git` folder in the directory. Please don't manually change/modify/delete the `.git` folder.
- `git clone` (only used when pulling remote repository) cause you want to download the remote repository to your local repository. (From remote server to local computer/machine)

### 4.4 Git local working flow

![](https://i.imgur.com/SWiLkCZ.png)

Local commit (also called checkin) has two steps:

![](https://i.imgur.com/X3BMqPn.png)

- Step one: stage  
  - You can use command line interface or VS Code to stage the file.
    - stage: `git add <filename>`
    - unstage: `git rm --cached <filename>`
      - --cached: this is a flag to tell Git(the program) to remove the file from the staging area, but not from the working directory.
      - If you don't use --cached, git will not track the file, and it's not used in most cases.
    - You can use `git status` to check the status of the local repository: whether a file is untracked or modified. 
      - U - Untracked  
      - A - Add 
      - M - Modified  


- Step two: commit
  - In command line interface
    - `git commit -m "message"`
      > message must be written, and it must be meaningful
    - `git log` is to show the commit history
        > Question：After `git commit`, can I use `git rm` to remove the file?  
        > Answer：Yes

You can absolutely remove files after committing:

1. **Remove files from working directory AND git:**
```bash
# Remove file from both working directory and git tracking
git rm file.txt
git commit -m "Removed file.txt"
```

2. **Remove files from git tracking only:**
```bash
# Remove file from git tracking only
git rm --cached file.txt
git commit -m "Removed file.txt from git tracking"
```

3. **Remove after commit:**
```bash
# First commit
git add file.txt
git commit -m "Add file"

# Later remove it
git rm file.txt
git commit -m "Remove file"
```


Important Notes:
- You can remove files at any time
- Each removal can be committed as a new change
- Use `git rm --cached` to untrack without deleting
- All changes are recorded in git history

- You can also check and operate git commit in the Source Control panel on the left side of VS Code.

![](https://i.imgur.com/Ucm4mQx.png)

Commit message can follow the following format:

![](https://i.imgur.com/rUFmdgJ.png)

But usually you can follow the company's template.

> Useful VScode Git plugin  
https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory

The general workflow in work:

1. git checkout -b feat/XX-NUM-UPDATE
2. working on the task, make changes on files
3. select, pick changed file and stage files
    - git add "fileName"
4. add commit msg
    - git commit -m "..."
    - enter msg in source control, and tick
5. publish/push
    - git push --
    - publish in sc
6. create pull request

### 4.5 `Git stash` Command
`git stash` is a temporary storage area, it will not be entered into the version control history
  - `git stash list` - check the stash list
  - `git stash pop` - get the latest stash
  - `git stash apply {stash-id}`
> stash is used between commit, when you have written but not yet committed

> Speaking of this, I wandered about if there could be any accidents. I have a friend told me that he made a mistake because he always did `git stash` there was a time he was called for a bug fix and he did `git stash` as usual but later he came back and did something and the whole day or a few days of work were gone. he learned from a hard way that `git stash` is not `git commit`


⚠️ **WARNING: Common Pitfalls with `git stash`**

`git stash` is temporary storage and can lead to lost work if not used carefully:

In this note, I would suggest you think about how long you can come back to the branch. if it is long, you can use `git commit` instead.

```bash
# Scenario that can lead to lost work:
git stash                  # Stash current changes
git checkout other-branch  # Switch to fix a bug
# ... time passes, maybe days ...
git stash clear           # Accidentally clear all stashes
# Or
git stash                 # New stash overwrites memory of old stash
# Original work is now lost!
```

Best Practices to Avoid Losing Work:
1. **Prefer commits over stashes for important work:**
```bash
# Better approach for work in progress
git add .
git commit -m "WIP: Feature in progress - saving before switching tasks"
```

2. **If using stash, be explicit:**
```bash
# Name your stash
git stash save "Feature A work in progress"
git stash list  # Check what's stashed
```

3. **Use stash sparingly:**
- Only for very temporary storage (minutes/hours, not days)
- For quick branch switches
- For minor interruptions

4. **Always check stash contents:**
```bash
git stash list            # List all stashes
git stash show stash@{0}  # Show contents of latest stash
```

5. **Consider stash alternatives:**
```bash
# For work in progress, create a temporary branch
git checkout -b temp-save-work
git add .
git commit -m "Temporary save"

# Later, you can:
git checkout original-branch
git merge temp-save-work   # Or cherry-pick commits
```

Remember:
- `git stash` is NOT a replacement for commits
- Stashes can be lost or overwritten
- Stashes are harder to recover than commits
- For important work, always commit


### 4.6 Undo Change
![](https://i.imgur.com/T4ksx3M.png)

- `git checkout .` you can restore the local working directory to the latest version
  - Or you can in VScode Source Control Panel to discard any files 
- `git clean` is to remove any files that are not in the commit history
  - It may prompt an error: refuse to clean where you can perform `git clean -f` to force clear




- `git revert` is to roll back, revert will record the rollback action, and create a new commit, so you can use it.
  - `git revert <SHA>`
  - revert can revert revert

![](https://i.imgur.com/HxPDnMq.png)

git revert 用一个新的commit来对历史记录进行回滚

```bash
# Initial timeline:
A -> B -> C -> D (HEAD)

# After reverting commit C:
A -> B -> C -> D -> C' (HEAD)
# Where C' is a new commit that undoes changes from C
```

1. **Single Commit Revert:**
```
Before:
A -> B -> C (bad commit) -> D (HEAD)

After git revert C:
A -> B -> C -> D -> C' (HEAD)
# C' undoes changes from C
```

2. **Multiple Commit Reverts:**
```
Before:
A -> B -> C -> D -> E (HEAD)

After reverting C and D:
A -> B -> C -> D -> E -> D' -> C' (HEAD)
# D' undoes D
# C' undoes C
```



- `git reset` is also perform the rolling back to a specific state of working directory BUT some companies don't allow you to do `git reset`, because reset is not revert. So only `git checkout <SHA>` is allowed to roll back to a specifci state of working directory

![](https://i.imgur.com/kG7VB4x.png)

- when you  use `git reset`, you are actually deleting the commit history, it is not going back to a specific commitso it's not allowed in some companies. It means you would lose the commit history.



⚠️ **WARNING:** `git reset` modifies history and can be dangerous. Many companies prohibit its use on shared branches.

#### Visual Timeline:
```bash
# Starting point:
A -> B -> C -> D (HEAD)

# After reset to B:
A -> B (HEAD)
# C and D commits are removed from history
```

You will lose the C and D commits!


`git soft reset` 

- Moves HEAD to specified commit
- Keeps all changes in staging area
- Safe for local work


```bash
# Example Timeline for Soft Reset:
Before:
A -> B -> C -> D (HEAD)
# Files: file1.txt, file2.txt committed in C and D

After git reset --soft B:
A -> B (HEAD)
# Changes from C and D are in staging area
# file1.txt and file2.txt are staged, ready to commit
```


```bash
# Common Soft Reset Usage:
# Combine last 3 commits into one
git reset --soft HEAD~3
git commit -m "Combined three commits into one"

# Fix commit message
git reset --soft HEAD~1
git commit -m "Better message"
```


`git hard reset`

- Moves HEAD to specified commit
- ⚠️ Deletes all changes
- ⚠️ Very dangerous - cannot recover changes

```bash
# Example Timeline for Hard Reset:
Before:
A -> B -> C -> D (HEAD)
# Files: file1.txt, file2.txt with changes

After git reset --hard B:
A -> B (HEAD)
# ⚠️ Changes in C and D are PERMANENTLY DELETED
# file1.txt and file2.txt return to state at commit B
```

 Best Practices:

1. **Before Any Reset:**
```bash
# Create backup branch
git branch backup-before-reset
```

2. **Safe Usage:**
```bash
# Prefer soft reset for local changes
git reset --soft HEAD~1

# Use revert for shared branches instead of reset
git revert HEAD
```

Key Differences from Reset:
```bash
# Reset (changes history):
A -> B -> C -> D -> E  # Before
A -> B -> C            # After reset to C

# Revert (adds new commits):
A -> B -> C -> D -> E  # Before
A -> B -> C -> D -> E -> E' -> D' # After revert
```


### 4.7 Some other commands 

![](https://i.imgur.com/3mtOm0r.png)

-  `git push origin`

- Text based log history： `git log`

![](https://i.imgur.com/HXFgtvg.png)

- Graphical log history：`git log --all --decorate --oneline --graph`

![](https://i.imgur.com/hVHManA.png)


- You can use `git diff <SHA> <SHA>` to compare two versions

```diff
diff --git a/file.js b/file.js
index 123456..789abc 100644
--- a/file.js
+++ b/file.js
@@ -1,5 +1,5 @@
-function oldName() {
-    return "old";
+function newName() {
+    return "new";
 }
 
-const value = 123;
+const value = 456;
```



2. **Compare Branches**
```bash
# Compare current branch with main
git diff main

# Compare two branches
git diff feature1..feature2
```

3. **Compare Specific Files**
```bash
# Compare single file with last commit
git diff file.js

# Compare file between commits
git diff abc123 def456 file.js
```

4. **Compare Staged Changes**
```bash
# Show what will be committed
git diff --staged
```



- You can use graphical interface to compare like the extension `Git Graph` https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory

![](https://i.imgur.com/0Az4SlW.png)


- You can use `git blame`, to find someone's code problem
  - You can view file history or view line history by right-clicking the code

In VScode, you can use `GitLens` extension to show blame information inline
```bash
# GitLens (Recommended)
- Shows blame information inline
- Hover over lines to see detailed history
- Shows authors and dates in the editor
```

```bash
# Basic blame for entire file
git blame filename.js

# Output example:
^5789abc (John Doe     2023-01-10 10:00:00 +0000  1) function hello() {
^5789abc (John Doe     2023-01-10 10:00:00 +0000  2)   console.log("Hello");
a123bcde (Jane Smith   2023-02-15 11:30:00 +0000  3)   return true;
^5789abc (John Doe     2023-01-10 10:00:00 +0000  4) }

# Blame specific lines
git blame -L 10,20 filename.js

# Show email addresses
git blame -e filename.js

# Ignore whitespace changes
git blame -w filename.js
```



## 5. Branch and Merge

![](https://i.imgur.com/X2t0yI3.png)


### 5.1 How to create a branch:
- `git checkout -b <branchName>`

  > It is recommended that when any developer receives any new task or ticket, they need to create a new branch and name it with the ticket number.

  > Everyone use different branch

  > You can pull someone's branch but please don't do any modifcation. if you need to modify code, then you need to create your own branch 

  > branch naming has to be meaningful; Naming convention is always followed by the company's policy or team's policy
  > 举例：`<ticket>/<ticket-number>-<title>`  
  > 举例：`feat/JR-101-create-for-home-page`

Switch branch 切换 branch
- `git checkout <branchName>`
or `git swtich <branchName>`

Delete branch 删除 branch
- `git branch -D <branchName>`
  > In company, we only create branch but not delete branch 


> Personal notes: I also work in a company that only keep main branch and don't push any branch to remote repository 

### 5.2 Merge

merge from - `git merge <branchName>`


> Because at work each day there will be people to commit/push code. Hence a good habit is to `git pull` from the remote each day when you start and also do `git merge` to your own branch to continue to work so that it will have less chance to encounter conflict when you merge in the end (因为每天都有人提交代码，所以每天上班都从master branch拉取最新的代码，并merge到自己的branch上，然后开始工作，这样才不会冲突并基于最新的代码。)
>  - Sometimes conclift will occur when you `git pull` it is normal.
>  - If conflict, you can just trouble shoot in time \
>  - Above all, you need to commit/push from time to time, please don't wait for the end to push

> git visualisation：https://git-school.github.io/visualizing-git/#free


## 6. Remote working and team collaboration 
### 6.1 Pull 和 Push

In general, the repository already exists in the company, so you can clone the remote repository to your local:

- `git clone <url>`
  > Do not try `git clone ` inside a `git` repository because it will create a nested  `git` repository 

Example of problematic nested structure:
```bash
parent-repo/           # Has .git folder
  ├── .git/
  ├── src/
  │   └── other-repo/ # Another .git folder here - PROBLEMATIC!
  │       ├── .git/   # Nested git repository
  │       └── code.js
  └── README.md
```

Problems with nested repositories:
1. Confusing git status reports
2. Unclear which .git directory is being used
3. Potential conflicts between parent and child repos
4. Complicated commit history
5. Push/pull complications



- 使用 `git remote -- verbose` print detailed information
  > default remote is called origin  
  > `origin` usually from Github, or from self-hosted Git Server
  > git clone from origin

- Publish Branch：You push your local branch to remote 
- Fetch: pull metadate but not sync You can see the difference between local branch and remote branch but not doing merge; 
- In VScode, the button `sync changes` is equal to push

How to submit your code to main branch 
- You need to create a Pull Request（short for PR） 
  > Description Markdown  
  > usually company will provide you a template  
  > Some process will have people to review and test
  > You can specify reviewer
  > After the reviewer completed the review, the PR creator has to do click `rebase and merge 




### .gitignore 文件

Sometimes, you will have some files that you don't want to commit to remote repository. You can write them in `.gitignore` file. You can use wildcard `*` as it means "anyname" of the same file type
```
 *.mp3
 *.mp4
 *.dll
 *.dov
 *.docx
 *.xlsx
 *.pptx
 */lib/*
 */bin/*
 .DS_Store
```
> GitHub has a template for `.gitignore`

### Rebase and Merge

In Git, `merge` and `rebase` are both commands used to merge changes from one branch into another, but they work differently.
 
However, they have fundamentally different effects on the commit history. For the most of time, you only need to use `git rebase` since it will create a linear commit history. In the future, we can do audit on the commit history. Be kind to your future self.

1. Merge 合并：

- How it works: Merge will combine two branches as well as their commit history into one new commit 

```bash
# Before merge:
main:     A -> B -> C     # Main branch has commits A, B, C
          \               # Branch point from A
feature:   D -> E         # Feature branch has commits D, E

# After merge:
main:     A -> B -> C -> M   # Main now includes merge commit M
          \            /     # The '/' shows branches reconnecting
feature:   D -> E ----      # Feature branch ends at merge point
```

What this means:
1. **Branch Creation**
   - Started at commit A
   - Main branch continued with B, C
   - Feature branch created from A, added D, E

2. **During Merge**
   - **Git finds common ancestor (A)**
   - Combines changes from both paths:
     - Main path (A → B → C)
     - Feature path (A → D → E)

3. **After Merge**
   - New merge commit 'M' is created
   - 'M' has two parents:
     - Parent 1: C (from main)
     - Parent 2: E (from feature)
   - All history is preserved
   - You can trace back through either path


After a merge, you can trace back through either path using various git commands:

1. **Using `git log --graph`**
```bash
# Show visual representation of all paths
git log --graph --oneline --all

* abc123 (HEAD -> main) Merge branch 'feature'    # Merge commit M
|\
| * def456 (feature) Add feature E                # Feature path
| * ghi789 Add feature D
* | jkl012 Add main C                            # Main path
* | mno345 Add main B
|/
* pqr678 Initial commit A                         # Common ancestor
```

- `* |` means "this commit is on main branch, and feature branch exists in parallel"
- `| *` means "this commit is on feature branch, and main branch exists in parallel"


1. **Main Branch Path (through first parent)**
```bash
M -> C -> B -> A
git log --first-parent main
```

2. **Feature Branch Path (through second parent)**
```bash
M -> E -> D -> A
git log abc123^2  # Start from second parent of merge
```

3. **View Merge Details**
```bash
git show abc123   # Shows merge commit M details
# Merge: jkl012 def456  # Shows both parent commits (C and E)
```

After a merge you will see  the merged commit in the git commit history because merge will create a snapshot of the two branches. `git merge`  will keep the  changes of each branch separately. This means you can see the original branch history and changes in the branch.

Pros and Cons of Merge:

| Pros | Cons |
|------|------|
| Easy to understand and use | Becomes complex with many branches |
| Preserves complete branch history | Can create "spaghetti history" with multiple merges |
| Creates clear snapshots of merged states | Merge commits can clutter commit history |
| Safe and non-destructive | Can be difficult to read with parallel development |
| Maintains clear record of parallel development | Complex to trace specific changes across merges |


Following what we learned previously, when assigned a a new task, you will create a new branch and work on it. 
![](https://i.imgur.com/o2Cz8Uo.png)

Let's say you finish the task and ONLY do `git merge` to main branch. In this case, Ray showed us an examples of a P3 project he was leading. There were 451 branches! it means you will have 451+ branches to merge to main branch.

![](https://i.imgur.com/IKI4KWs.png)

![](https://i.imgur.com/StMc6et.png)


Because we  are working in a team and there are chances that we  are working on the same file which means it is possible that we edit the same lines of code. 

the chance that conflict when we merge the branch to main branch occurs is high.

![](https://i.imgur.com/nM65jgA.png)


incoming change refers to changes from the branch feature1, it means on the line 9  `<h1>`....
however the changes from the main branch, the line 9 is  `<span>`. In this case, git won't know which one to keep or which one to discard. Hence conflict occurs.

In most of cases, you can delete all and rewrite the whole things. For example, person A work on an algorithm, whereas person B work on another algorithm. They both solve a same problems but from different situations or different user cases.

As for your task, you may need to understand what they are doing and then delete all and rewrite the whole things to combine these two situations with their two algorithms.

Side note: If you are the first person to merge your branch to main branch, it means you may not need to worry about conflict. So last merge, last to close laptop to have a good sleep.


2. Rebase (变基)

- How it works: Rebase is to change the base of the branch on top of the latest commit of another branch. Hence you will have a linear commit history.

Example:


Effect/Result of Rebase:
Rebase creates a linear branch history that looks cleaner, without merge commits. It "moves" the current branch's commits to the tip of another branch, maintaining commit order and providing a clearer commit history.

Visual Example:
```bash
# Before rebase:
main:     A -> B -> C
          \
feature:   D -> E

# After rebase:
main:     A -> B -> C
                     \
feature:               D' -> E'
# Note: D' and E' are new commits with same changes as D and E
```

1. Feature branch splits from A 
2. After rebase, the feature branch is re-based on top of C
3. D' and E' are new commits with the same changes as D and E, but with new commit hashes

Pros and Cons of Rebase:

- Pros: Rebase can create a linear commit history, which is easier to understand and maintain.
- Cons: Rebase can cause conflicts and modify commit hashes, which can be problematic in public branches.


```bash
# Before rebase:
feature: A -> B (abc123) -> C (def456)

# After rebase:
feature: A -> B (xyz789) -> C (uvw012)
# Same changes but DIFFERENT commit hashes!
```

Problems with Public Branches:
```bash
# Developer 1:
git checkout feature
git rebase main
git push -f  # Forces push because history changed

# Developer 2 (who already has the old version):
git pull  # CONFLICT! Local history doesn't match remote
# Their local: A -> B (abc123) -> C (def456)
# Remote:     A -> B (xyz789) -> C (uvw012)
```
In this case, developer 2's local history where commit B is different from remote B and so they will have to resolve conflicts and merge the changes again.


Example of What Can Go Wrong:
```bash
# Timeline of Problems:
1. Team has feature branch: A -> B -> C
2. Dev 1 pulls feature branch
3. Dev 2 pulls feature branch
4. Dev 1 rebases and force pushes
5. Dev 2's work is now based on "ghost" commits

# Dev 2's Situation:
Local:  A -> B -> C -> D        # Their new work
Remote: A -> B' -> C' -> E      # Rebased branch
# Result: Complete mess to resolve
```

Safe vs Unsafe Rebase:

Safe (Local Branch):
```bash
# Working alone on feature branch
git checkout feature
git rebase main
git push  # Only if you haven't pushed feature before
```
Unsafe (Public Branch):
```bash
# DANGER: Others are using this branch
git checkout shared-feature
git rebase main
git push -f  # Forces others to resolve conflicts
```


Best Practices to Avoid Problems:

1. **Golden Rule:**
```bash
# Never rebase branches that others are using
# Only rebase your local, unpublished work
```

2. **If You Must Rebase Public Branch:**
```bash
# 1. Notify team
# 2. Everyone commits their work
# 3. Team stops working on the branch
# 4. Perform rebase
# 5. Team re-clones or resets their local copies
```

3. **Recovery If Things Go Wrong:**
```bash
# Find old commits in reflog
git reflog

# Reset to before rebase
git reset --hard HEAD@{2}

# Or create new branch from old commits
git checkout -b backup-branch HEAD@{2}
```

- Rebase rewrites history
- New commits = new hashes
- Force push required after rebase
- Can break team collaboration
- Use with caution on shared code



Summary:
When using Merge:
- Preserves complete branch history
- Suitable for collaborative development on public branches
- Results in multiple parallel history lines

When using Rebase:
- Creates a linear commit history
- Provides cleaner and more organized commit history
- Must be used with caution, avoid rebasing public branches
- Results in a single linear history line

 > Use https://git-school.github.io/visualizing-git/#free practice



git commit for both

![](https://i.imgur.com/lwnk20p.png)
on your left, it is the commit history of the main branch
on your right, it is the commit history of the feature branch





![](https://i.imgur.com/ME4ijtV.png)
So far the commit history are the same.


![](https://i.imgur.com/KSDHwTj.png)


![](https://i.imgur.com/PwJaYz0.png)

now we need to compare merge and rebase


Merge 
![](https://i.imgur.com/AJbCrZ2.png)



Rebase

![](https://i.imgur.com/VVs9v2H.png)

We rebase on master, the original base commit is ce04...., now the new base commit is edfa...


Let's continue.


![](https://i.imgur.com/x7QzdJm.png)
We continue to commit 3 times after merge. Now you can start to see how complex it could be if we merge


Let's see rebase after 3 commits

![](https://i.imgur.com/a3D7ZEX.png)

See, rebase is much cleaner. it is a linear commit history.



### Push May Be Rejected After Local Reset
When you reset locally and try to push, your push might be rejected. While you can use `git push -f` (force push), it's generally not recommended.

⚠️ **WARNING: Force Push Dangers**
```bash
# Scenario that can cause problems:
git reset --hard HEAD~1     # Local reset
git push                    # Gets rejected
git push -f                 # DANGEROUS! Overwrites remote history

# Why it's dangerous:
1. Erases remote commits
2. Breaks other developers' history
3. Can cause lost work for team members
```

Safer Alternatives:
```bash
# Instead of reset + force push, consider:
git revert HEAD            # Creates new commit that undoes changes
git push                   # Safe, preserves history

# Or if you must reset:
git checkout -b backup     # Create backup branch
git reset --hard HEAD~1    # Then do reset
git push origin backup    # Push backup branch first
```

Best Practice:
- Avoid force push on shared branches
- Use `revert` instead of `reset` when possible
- Always communicate with team before force pushing
- Create backup branches before destructive operations



 
### Github Pull Request

When you have a local branch and you want to push it to remote and then you want to create a pull request.

![](https://i.imgur.com/LaubV1b.png)

You can click the `Pull Request` button on the right top corner. or going to the tab on the middle of the page to manunally create a pull request.

Ticket naming and description
![](https://i.imgur.com/67xYoKi.png)


this is because git is a version control system. we have lots of different versions of the code on one branch - main branch usually is the production branch.
On production branch, we need to make sure it is stable and working. so there will be many tests and checks.

in lots of companies, they will have a QA team to test the code and also a release manager to release the code to production. a senior developer will review the code and then merge the code to production branch.

![](https://i.imgur.com/lCDIbkP.png)



Normal developers won't have the permission to merge to production branch. Hence you need to create a pull request to merge your branch to production branch.


![](https://i.imgur.com/uMJ1NC8.png)


so when you create a pull request, you need a person to approve it and usually reviwer. 



LGTM short look good to me



![](https://i.imgur.com/rm7CZFE.png)


If you are the one who created the PR, you are responsible for clicking and merging the PR.

If a company has a good system and workflow, they should have better understanding of each part of tasks so conflicts are avoided



### `git push -f`


![](https://i.imgur.com/DuJ8piH.png)

So we have 3 commits on the local branch.
![](https://i.imgur.com/px8FFei.png)

if you `git reset`, because you want to rewrite something in your source code files.


![](https://i.imgur.com/Y84gcbV.png)

If you fix some bugs, and then commit it again. However, your local machine will have a different commit history than the remote one. In your local machine, you will see (向下1， 向上1)

if you push it,    it will be rejected.

![](https://i.imgur.com/OSG1KgH.png)

because the middle one is not on the remote branch and you don't want it. 

you can use `git push -f` to force push it. so the middle one will be erased.

