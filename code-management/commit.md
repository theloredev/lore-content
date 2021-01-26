---
id: commit
title: Commit
sidebar_label: Commit
---

## When/How to Commit?
- Commit after completing a task/problem.
- Have to transition to something else due to an urgent issue quickly? Many Code Management Systems support ["stashing"](#stashing) your current changes so you can pick them up later without polluting your commit history with incomplete work.
- When dealing with large changes, it's important to divide your work into smaller chunks and commit a part or logical portion of the related changes when completed.
- Commit Related Changes: A commit should exclusively contain related changes. Do not commit two separate, unrelated bugs, into a single commit.
- Write Good Messages: You should write short and descriptive messages for each of your commits. Avoid long messages but be descriptive of what is being done.
- Test Before You Commit: Commit code you are confident works, and that has been tested. This can be any combination of unit tests or functional tests. You should review your changes prior to committing. I can't tell you how many times I've quickly compared my changes against the last committed code and spotted an unnecessary logging statement or a few lines of old code I've commented out.

Help yourself by following these best practices. When something breaks, it will be easier to track down exactly when and where the issue was introduced and revert the individual change.


## Commit often

There are several reasons why you should commit your changes frequently. We all have started developing something, only to find that it isn’t going to work after all. 

- You can easily roll your codebase back to an earlier revision and get back to work by having frequent commits.  
- After you commit changes to a branch, you merge in the source branch, saving you from merge nightmares.
- Finally, you should commit individual features or discrete units of work.

## Know what to ignore

All code management systems have a way to ignore specific files, file types, and folders. Some general rules on what should be ignored and not included in your committed codebase are:
- Any local configuration files specific to your machine
- Any IDE created files
- Any downloaded dependencies
- Any compiled code that comes from your codebase
    - For example, many Java web applications will compile the Java source code into a “target” directory. That directory should be ignored.
- Any operation system generated files

## Stashing

Stashing allows saving uncommitted work on a branch for later use without committing to your branch. Once your work is stashed, the branch you are on is then reverted to the last commit. It is completely clean and free from any of the changes you stashed away. Additionally, you can “pop” your stashed changes back into your branch and pick up where you left off.

Your stashed changes remain strictly on your local computer and are not pushed to a remote code management system server.

An example scenario is when you are developing a feature on a branch, and suddenly, an urgent bug is reported that requires your immediate attention. The work on your feature is not at a point where it should be committed. The solution is to stash your changes, and then you are free and clear to take care of the bug. Your feature changes are safely saved away. Once the bug is resolved, you can pop your stashed changes and pick up where you left off.