---
id: commit-completed-work
title: Commit Completed Work
sidebar_label: Commit Completed Work
---

You spent your afternoon constructing a solution to a problem and you feel that it completes your task. This is an ideal time to commit your work and call it a day.  Of course, there are times where you are halfway through developing a solution, and an urgent issue has come along and you have to quickly transition to something else. Many Code Management Systems support the notion of “stashing” your current changes so you can pick up where you left off later (more on this concept later). This way, you don’t pollute your commit history with incomplete work.

Now, what do you do when you have a larger change? The solution here is to divide your work into smaller chunks, and when a part or logical portion of related changes are complete, commit them.
- Commit Related Changes - A single commit should exclusively contain related changes. For example, if you are resolving two separate, unrelated bugs, it doesn’t make sense to commit your changes in a single commit.
- Write Good Messages - You should write short, and descriptive messages for each of your commits. There is no need to write an essay with each commit, but you do need to be descriptive about what is being checked in.
- Test Before You Commit - When you commit code, you should be confident in saying that it works because it has been tested. This can be any combination of unit tests or functional tests, but you should also review your changes prior to committing. I can’t tell you how many times I’ve quickly compared my changes against the last committed code and spotted an unnecessary logging statement or a few lines of old code I’ve commented out.

Following the last few best practices have a really great side effect. When something breaks, it can be easier to track down exactly when and where the issue was introduced, and that individual change can be reversed.
