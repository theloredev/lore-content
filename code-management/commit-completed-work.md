---
id: commit-completed-work
title: Commit Completed Work
sidebar_label: Commit Completed Work
---

## When/How to Commit?
- Commit after completing a task/problem.
- Have to transition to something else due to an urgent issue quickly? Many Code Management Systems support ["stashing"](#stashing) your current changes so you can pick them up later without polluting your commit history with incomplete work.
- When dealing with large changes, it's important to divide your work into smaller chunks and commit a part or logical portion of the related changes when completed.
- Commit Related Changes: A commit should exclusively contain related changes. Do not commit two separate, unrelated bugs, into a single commit.
- Write Good Messages: You should write short and descriptive messages for each of your commits. Avoid long messages but be descriptive of what is being done.
- Test Before You Commit: Commit code you are confident works, and that has been tested. This can be any combination of unit tests or functional tests. You should review your changes prior to committing. I can't tell you how many times I've quickly compared my changes against the last committed code and spotted an unnecessary logging statement or a few lines of old code I've commented out.

Help yourself by following these best practices. When something breaks, it will be easier to track down exactly when and where the issue was introduced and revert the individual change.
