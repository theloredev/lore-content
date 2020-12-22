---
id: branching-&-workflow-strategies
title: Branching & Workflow Strategies
sidebar_label: Branching & Workflow Strategies
---

There are numerous Code Management Systems, and each has its own strategies and techniques regarding how to go about handling branches. While the nuances of each system are unique, many of the general concepts are universal.

At present, the most popular Code Management System is Git, so this handbook will utilize Git as the basis for this section.

## Why Branch?

Below are just a few of the reasons why branching is a good practice to get in the habit of.
- Allows multiple developers to work concurrently without stepping on each other's changes.
- Allows for multiple streams of work to remain independent.
- Adds to overall stability of the central codebase.
- Easier to collaborate, as developers can easily push changes to the central repository so other developers can pull the branch down to work on it.

## Common Branch Types

It should be noted that all branch types function and operate exactly the same way. The different types, or classifications, are used to provide clarity for users and are helpful when defining workflow processes.
- Top Level Branch: This is the main code branch, where all other branches descend from. In Git repositories, this is often named “master” by default.
- Development: Many times shortened to “dev” or “develop,” this branch can be used for any active development that is being performed.
- Staging: This type of branch is typically used for a non-production environment.
- Release: These branches are often temporary, and meant to lead up to a specific release.
- Feature: Branches of this type are used for any enhancements, features, or new development that are being done in the codebase. Feature branches are often cut from develop branches. These branches are short lived, and are closed once they are merged into their parent branch.
- Bug: Often created to manage the resolution of a bug, many times from a non-production source branch. Their flow is fairly similar to that of feature branches.
- Hotfix:This type branch is often used to merge an urgent fix directly into the top level branch. This branch is cut from the top level branch, and may have to be carefully merged back into develop.

## Renaming the Master Branch

In recent years, there has been some well deserved criticism and consideration given to microaggressions commonly used in the IT world. One of those is the use of “Master” to describe a top level relationship. The use of Master, along with Master & Slave comes with a great deal of cultural sensitivity, particularly within the United States.

With that in mind, consider refraining from naming and referring to your top level branch as “master” and instead consider a neutral nomenclature, such as “primary” or “main.”

## Branching Workflows

There are several different Git branching strategies that help to standardize the flow of new code into the codebase. Below are a few common strategies that are often used. There are many more that can be found in the links below. 

### Gitflow

In this model, there are two permanent branches, primary and develop. Primary is used for production releases, and develop is where development work is done.  It also utilizes feature, release, bug, and hotfix branches.

This workflow starts with the develop branch, then feature branches are cut from develop by developers.  Once a sufficient number of feature branches have been merged into develop, a release branch can be created.  That release branch can be tested, fixed via bug branches, and eventually a new primary branch is created from the release branch, and deployed into production.

Hotfixes are then utilized to resolve any issues with this primary branch, and back-merged into the develop branch.

This workflow is based off of the scheduled deployment strategy.

### Github Flow

This workflow is ideal for frequent delivery in a continuous delivery model. There is only one permanent branch, the primary branch.  From this primary branch, feature branches are cut and all development work is performed in these branches.

When development is complete, the feature branch is pushed to the remote repository and deployed into a non-production environment. It is tested, and merged into the primary branch if no problems are found.

If there is an issue, then the primary branch is redeployed, since it is always kept in a working state.

This workflow is based off of the Branch-Per-Feature deployment strategy.

### Gitlab Flow

This workflow uses the concept of a location or snapshot for several of its permanent branches.  With this model, if you have production, stage, and development environments, then there would be a primary, stage, and develop permanent branches.

Feature branches are cut from develop, and once work has been completed and tested, it is merged into develop. From there, develop is merged into stage, and then stage is merged into primary, and released to production.

This workflow is based off of the state branching strategy.

Sources: https://pradeeploganathan.com/git/git-branching-strategies/,  
https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow,  
https://www.atlassian.com/git/tutorials/what-is-version-control,  
https://en.wikipedia.org/wiki/Version_control  
