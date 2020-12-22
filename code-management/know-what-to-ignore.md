---
id: know-what-to-ignore
title: Know What To Ignore
sidebar_label: Know What To Ignore
---

All code management systems have a way to ignore specific files, file types, and folders. Some general rules on what should be ignored and not included in your committed codebase are:
- Any local configuration files specific to your machine
- Any IDE created files
- Any downloaded dependencies
- Any compiled code that comes from your codebase
    - For example, many Java web applications will compile the Java source code into a “target” directory. That directory should be ignored.
- Any operation system generated files
