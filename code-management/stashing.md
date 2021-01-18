---
id: stashing
title: Stashing
sidebar_label: Stashing
---

Stashing allows saving uncommitted work on a branch for later use without committing to your branch. Once your work is stashed, the branch you are on is then reverted to the last commit. It is completely clean and free from any of the changes you stashed away. Additionally, you can “pop” your stashed changes back into your branch and pick up where you left off.

Your stashed changes remain strictly on your local computer and are not pushed to a remote code management system server.

An example scenario is when you are developing a feature on a branch, and suddenly, an urgent bug is reported that requires your immediate attention. The work on your feature is not at a point where it should be committed. The solution is to stash your changes, and then you are free and clear to take care of the bug. Your feature changes are safely saved away. Once the bug is resolved, you can pop your stashed changes and pick up where you left off.