---
id: branching-&-workflow-strategies
title: Branching & Workflow Strategies
sidebar_label: Branching & Workflow Strategies
---

There are numerous Code Management Systems, and each has its own strategies and techniques regarding how to handle branches. While the nuances of each system are unique, many of the general concepts are universal.

At present, the most popular Code Management System is Git; therefore, this handbook will utilize Git as the basis for this section.

## Why Branch?

A few reasons why branching is a good practice:
- Allows multiple developers to work concurrently without stepping on each other's changes.
- Allows for multiple streams of work to remain independent.
- Adds to the overall stability of the central codebase.
- It's easier to collaborate. Developers can easily push changes to the central repository, while others can pull the branch down to work on it.

## Common Branch Types

It should be noted that all branch types function and operate exactly the same way. The different types, or classifications, are used to provide clarity for users and help define workflow processes.
- Top Level Branch: The main code branch, all other branches descend from it. In Git repositories, it's often named "master" by default.
- Development: Many times shortened to "dev" or "develop". This branch can be used to perform any active development.
- Staging: Typically used for a non-production environment.
- Release: Often temporary and meant to lead up to a specific release.
- Feature: Used for enhancements, features, or new development in the codebase. Feature branches are often cut from develop branches. They are short-lived and are closed once they merge into their parent branch.
- Bug: Often created to manage bug resolution, many times from a non-production source branch. Their flow is fairly similar to that of feature branches.
- Hotfix: Used to merge an urgent fix directly into the top-level branch. This branch is cut from the top-level branch and may have to be carefully merged back into development.

## Renaming the Master Branch

In recent years, there has been some well-deserved criticism and consideration given to microaggressions commonly used in the IT world. One of those is the use of "Master" to describe a top-level relationship. The use of "Master", along with "Master & Slave" comes with a great deal of cultural sensitivity, particularly within the United States.

With that in mind, consider refraining from naming and referring to your top-level branch as "master". Instead, consider a neutral vocabulary, such as "primary" or "main."

## Branching Workflows

Several different Git branching strategies help to standardize new code flow into the codebase. Below are a few common strategies. There are many more that can be found in the sources section at the bottom of the page. 

### Gitflow

This workflow has two permanent branches, primary and develop. Primary is used for production releases and develop for development work. It also has the feature, release, bug, and hotfix branches.

The workflow starts with the develop branch, then feature branches are cut from develop. Once a sufficient number of feature branches have been merged into develop, a release branch can be created. That release branch can be tested, fixed via bug branches, and eventually, a new primary branch is created from the release branch and deployed into production.

Hotfixes are used to resolve any issues with this primary branch and merged back into the develop branch.

This workflow is based on the scheduled deployment strategy.

### Github Flow

This workflow is ideal for frequent deliveries in a continuous delivery model. There is only one permanent branch, the primary branch.  From it, feature branches are cut, and all development work is performed.

When development is complete, the feature branch is pushed to the remote repository and deployed into a non-production environment. It is tested and merged into the primary branch if no problems are found.

If there is an issue, then the primary branch is redeployed since it is always kept in a working state.

This workflow is based on the Branch-Per-Feature deployment strategy.

### Gitlab Flow

This workflow uses the concept of a location or snapshot for several of its permanent branches.  With this model, if you have production, stage, and development environments, there would be a primary, stage, and develop permanent branches.

Feature branches are cut from develop, and once work has been completed and tested, it is merged into develop. From there, develop is merged into stage, and then stage is merged into primary, and released to production.

This workflow is based on the state branching strategy.

Sources:  
<a href="https://pradeeploganathan.com/git/git-branching-strategies/" target="_blank">https://pradeeploganathan.com/git/git-branching-strategies/</a>,  
<a href="https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow" target="_blank">https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow</a>,  
<a href="https://www.atlassian.com/git/tutorials/what-is-version-control" target="_blank">https://www.atlassian.com/git/tutorials/what-is-version-control</a>  
<a href="https://en.wikipedia.org/wiki/Version_control" target="_blank">https://en.wikipedia.org/wiki/Version_control</a>
