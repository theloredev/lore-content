---
id: example-doc
title: Code Management
sidebar_label: Code Management doc
---

Related Documents:

- [Core Skills](core-skills/example.md)
- [Development](development/example.md)
- [Testing](testing/example.md)

## Introduction

Code Management Systems, also known as Version Control Systems, have been around for quite a while, but despite that, there still is code sitting in shared folders, or in zip files that get passed around to different developers, and devoid of any sort of tracking, revisioning, or management.

If you are working in an environment like that, I greatly encourage you to find a Code Management System and transition the code into it. Many of them are low cost, and sometimes, free depending on the tier of service required.

Before you start running wild with your new, shiny management system, you should learn about how you should actually use it. Here are some best practices for using code management systems.

## Basic Features

Every Code Management System possesses a common set of features.  Those features include:

- Change history - A detailed record of every change that has been made to a file, including dates, user info, and a message to provide context as to why the change was made.

- This often includes the ability to compare various versions of a file, which can be useful when tracking when a change was made that introduced a bug.

- Branching & Merging - The ability to create offshoots, called branches, from the central codebase, as well as the ability to merge those branches back into the central codebase.

- Distributed/Remote - Many modern Code Management Systems are designed to run remotely/in the cloud.

- Integration with IDE's - While not a feature of the Management Systems themselves, many IDE's integrate with numerous different systems.

## Commit Often

There are a number of reasons why you should commit your changes frequently. First, we all have started developing something, only to find that it isn't going to work out at all. By having frequent commits, you can easily roll your codebase back to an earlier revision and get back to work.  A recommended best practice to get in the habit of is, after you commit changes to a branch, you merge in the source branch.  Doing this will help save you from merge nightmares.

Finally, you should commit individual features or discrete units of work.

## Commit Completed Work

You spent your afternoon constructing a solution to a problem and you feel that it completes your task. This is an ideal time to commit your work and call it a day.  Of course, there are times where you are halfway through developing a solution, and an urgent issue has come along and you have to quickly transition to something else. Many Code Management Systems support the notion of "stashing" your current changes so you can pick up where you left off later (more on this concept later). This way, you don't pollute your commit history with incomplete work.

Now, what do you do when you have a larger change? The solution here is to divide your work into smaller chunks, and when a part or logical portion of related changes are complete, commit them.

- Commit Related Changes - A single commit should exclusively contain related changes. For example, if you are resolving two separate, unrelated bugs, it doesn't make sense to commit your changes in a single commit.

- Write Good Messages - You should write short, and descriptive messages for each of your commits. There is no need to write an essay with each commit, but you do need to be descriptive about what is being checked in.

- Test Before You Commit - When you commit code, you should be confident in saying that it works because it has been tested. This can be any combination of unit tests or functional tests, but you should also review your changes prior to committing. I can't tell you how many times I've quickly compared my changes against the last committed code and spotted an unnecessary logging statement or a few lines of old code I've commented out.

Following the last few best practices have a really great side effect. When something breaks, it can be easier to track down exactly when and where the issue was introduced, and that individual change can be reversed.

## Know What To Ignore

All code management systems have a way to ignore specific files, file types, and folders. Some general rules on what should be ignored and not included in your committed codebase are:

- Any local configuration files specific to your machine

- Any IDE created files

- Any downloaded dependencies

- Any compiled code that comes from your codebase

- For example, many Java web applications will compile the Java source code into a "target" directory. That directory should be ignored.

- Any operation system generated files

## Stashing

Stashing allows you to take any uncommitted work on a branch, and save it away for later without actually committing it to your branch. Once your work is stashed, the branch you are on is then reverted back to the last commit. It is completely clean and free from any of the changes you stashed away. Additionally, you can "pop" your stashed changes back into your branch, and pick up where you left off.

Your stashed changes remain strictly on your local computer, and are not pushed to a remote code management system server.

An example scenario is when you are developing a feature on a branch, and suddenly, an urgent bug is reported that requires your immediate attention. The work on your feature is not at a point where it should be committed. The solution is to stash your changes, and then you are free and clear to take care of the bug, and your feature changes are safely saved away. Once the bug is resolved, you can pop your stashed changes, and pick up where you left off.

## Branching & Workflow Strategies

There are numerous Code Management Systems, and each has its own strategies and techniques regarding how to go about handling branches. While the nuances of each system are unique, many of the general concepts are universal.

At present, the most popular Code Management System is Git, so this handbook will utilize Git as the basis for this section.

### Why Branch?

Below are just a few of the reasons why branching is a good practice to get in the habit of.

- Allows multiple developers to work concurrently without stepping on each other's changes.

- Allows for multiple streams of work to remain independent.

- Adds to overall stability of the central codebase.

- Easier to collaborate, as developers can easily push changes to the central repository so other developers can pull the branch down to work on it.

### Common Branch Types

It should be noted that all branch types function and operate exactly the same way. The different types, or classifications, are used to provide clarity for users and are helpful when defining workflow processes.

- Top Level Branch: This is the main code branch, where all other branches descend from. In Git repositories, this is often named "master" by default.

- Development: Many times shortened to "dev" or "develop," this branch can be used for any active development that is being performed.

- Staging: This type of branch is typically used for a non-production environment.

- Release: These branches are often temporary, and meant to lead up to a specific release.

- Feature: Branches of this type are used for any enhancements, features, or new development that are being done in the codebase. Feature branches are often cut from develop branches. These branches are short lived, and are closed once they are merged into their parent branch.

- Bug: Often created to manage the resolution of a bug, many times from a non-production source branch. Their flow is fairly similar to that of feature branches.

- Hotfix:This type branch is often used to merge an urgent fix directly into the top level branch. This branch is cut from the top level branch, and may have to be carefully merged back into develop.

### Renaming the Master Branch

In recent years, there has been some well deserved criticism and consideration given to microaggressions commonly used in the IT world. One of those is the use of "Master" to describe a top level relationship. The use of Master, along with Master & Slave comes with a great deal of cultural sensitivity, particularly within the United States.

With that in mind, consider refraining from naming and referring to your top level branch as "master" and instead consider a neutral nomenclature, such as "primary" or "main."

### Branching Workflows

There are several different Git branching strategies that help to standardize the flow of new code into the codebase. Below are a few common strategies that are often used. There are many more that can be found in the links below.

#### Gitflow

In this model, there are two permanent branches, primary and develop. Primary is used for production releases, and develop is where development work is done.  It also utilizes feature, release, bug, and hotfix branches.\
This workflow starts with the develop branch, then feature branches are cut from develop by developers.  Once a sufficient number of feature branches have been merged into develop, a release branch can be created.  That release branch can be tested, fixed via bug branches, and eventually a new primary branch is created from the release branch, and deployed into production.

Hotfixes are then utilized to resolve any issues with this primary branch, and back-merged into the develop branch.

This workflow is based off of the scheduled deployment strategy.

#### Github Flow

This workflow is ideal for frequent delivery in a continuous delivery model. There is only one permanent branch, the primary branch.  From this primary branch, feature branches are cut and all development work is performed in these branches.

When development is complete, the feature branch is pushed to the remote repository and deployed into a non-production environment. It is tested, and merged into the primary branch if no problems are found.

If there is an issue, then the primary branch is redeployed, since it is always kept in a working state.

This workflow is based off of the Branch-Per-Feature deployment strategy.

#### Gitlab Flow

This workflow uses the concept of a location or snapshot for several of its permanent branches.  With this model, if you have production, stage, and development environments, then there would be a primary, stage, and develop permanent branches.

Feature branches are cut from develop, and once work has been completed and tested, it is merged into develop. From there, develop is merged into stage, and then stage is merged into primary, and released to production.

This workflow is based off of the state branching strategy.

Sources: <https://pradeeploganathan.com/git/git-branching-strategies/>,

<https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow>, <https://www.atlassian.com/git/tutorials/what-is-version-control>,

<https://en.wikipedia.org/wiki/Version_control>

## Commit

## Pull Requests

## Code Review

## Merging

## Tooling

---
