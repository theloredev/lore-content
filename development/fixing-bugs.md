---
id: fixing-bugs
title: Fixing Bugs
sidebar_label: Fixing Bugs
---

> "Program testing can be used to show the presence of bugs, but never to show their absence!" - Edsger W. Dijkstra

Bugs will be found in the software you and your team write. The hope is that most will be found during the QA process, as opposed to found by your end users. Regardless of when they are found, the task of fixing them may fall upon you, so you should learn some techniques to fix bugs more efficiently and effectively.

Points to write about…

- Replicate the bug
- Understand the problem as it is reported
- Track down the problem in the code
  - learn how to use your debugging tools
  - cast a wide net of breakpoints and narrow as you make your way through the code
  - if all else fails, dump as much data as you can to your logs
  - determine what kind of bug your dealing with
- Test your fix & try to break your fix!
- Add unit tests to make sure it never happens again
