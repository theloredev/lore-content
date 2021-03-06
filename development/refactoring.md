---
id: refactoring
title: Refactoring
sidebar_label: Refactoring
---

> "Refactoring has become a regular tool for any skilled programmer. However new people regularly enter our profession and need to learn about refactoring" -  <a href="https://martinfowler.com/" target="_blank">Martin Fowler</a>, Author of "Refactoring: Improving the Design of Existing Code"



## What is refactoring?

Refactoring is a series of techniques to alter code without changing its external behavior. The goal of refactoring is to improve the design and structure of the system. Refactoring code may involve rewriting code to enhance its clarity and efficiency, resolving bugs within the underlying code, and finally enhancing code to provide additional functionality.

## When should I refactor the code?

Refactoring code is an important part of Software Engineering, especially when we face some well-known situations like:

- Code with poor readability
- Duplicated code
- Buggy applications

The above situations can impact the time to develop new features. Robert C. Martin, the author of Clean Code, created this chart to show how crucial it is to create a clean codebase.

| ![](assets/development/refactoring/productivity-vs-time.png) |
|:--:|
| *Credit: Clean Code, Robert C. Martin, Chapter 1, page 35* |

This chart shows a real problem that could end up with a company shutting down. A situation Robert C. Martin has seen too often. Examining this chart, we see that as bad code increases, productivity decreases.

The ultimate goal is to write clean code the first time, to ensure the team does not suffer in the long run. It may take more time to write the initial code, but the added upfront cost far outweighs the potential future productivity impacts. 

In the end, the most important aspect to define if we should refactor the code or we shouldn't is the guarantee that our application will not have the same situation as this chart. Our application cannot be too hard to implement new features. Otherwise, the application might be doomed. Any effort is welcome to avoid this terrifying scenario!

Are you facing these problems: Code with bad readability, duplicated codes, application with a lot of bugs, and it's taking too much time to produce new releases? Every developer's goal as they work on a piece of code is to improve that code to make it better than the previous iteration. That may mean refactoring portions of a file while working on it to add a new enhancement.

## When should I not refactor code?

Consider the current business needs and what circumstances are necessitating a code change. There will be instances, like emergencies, that will make it impossible to have the time to refactor any code properly. Below you can find some situations that should refrain from refactoring code.

### The Manager said we don't have time

There will be instances when refactoring code will be a challenging, time-consuming task.  This is especially true if the team does not have a well-ingrained culture of refactoring and improving software. What should you do when the Manager or Product Owner says "no" to your request to spend time refactoring?

First, explain the possible scenario that we showed on this [chart](#when-should-i-refactor-the-code). We encourage you to have a good talk with the owners and managers to help them understand how crucial it is to get a quality codebase for the new features and enhancements. If they still say "no", accept it and keep delivering the best service you can.

### The code is clean and well implemented, but not written how you would do it

When we think about clean code and refactoring, we may turn to blog posts and articles from software engineers that we admire to enhance our skills on the subject. One challenge we may face is becoming overzealous with our desire to refactor everything we touch. This overzealousness may result in delays in our actual work and impacts on our projects as a whole.

Different developers may have different styles of coding. As long as the code is clean, well implemented, and complies with the agreed upon style guide, there may not be a need to refactor anything. Even your own code tomorrow may be better than your code from yesterday. Don't let the desire to refactor result in a delay on deliverables when it's not necessary.

## Red-Green Refactor

This concept incorporates using Test Driven Development (TDD) to implement the initial piece of software. This can only be used when unit tests have been written to validate and ensure the external behavior of the application.

| ![](assets/development/refactoring/tdd.png) |
|:--:|
| *Credit:  <a href="https://www.altexsoft.com/blog/engineering/code-refactoring-best-practices-when-and-when-not-to-do-it/" target="_blank">Code Refactoring: Best Practices, Altexsoft</a>* |

Here is the workflow:

- Write (or use) unit tests to ensure valid behavior before refactoring
- Refactor code
- May result in failing tests
- Refactor code
- Finally results in green tests

Our unit tests give us the ability to refactor code with much more confidence because we have the assurance that the code will be validated to ensure the system's behavior and stability. TDD is a great pattern for any software engineer to use, including when we need to refactor code.

## References

- <a href="https://www.altexsoft.com/blog/engineering/code-refactoring-best-practices-when-and-when-not-to-do-it/" target="_blank"><https://www.altexsoft.com/blog/engineering/code-refactoring-best-practices-when-and-when-not-to-do-it/></a>
- Clean Code, Robert C. Martin
- <a href="https://rubygarage.org/blog/when-to-refactor-code" target="_blank"><https://rubygarage.org/blog/when-to-refactor-code></a>


