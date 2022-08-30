---
id: technical-design
title: Technical Design
sidebar_label: Technical Design
---

Technical Designs are documents that auxiliate on definition and structure of our ideas in order to achieve a goal.

The creation of this document is crucial to structure ideas before implementing them. The final result consists in building software with more quality, teamwork and speed.

**Talk about other companies doing it**

# Benefits from Technical Designs

Software Engineering is not a simple task. There are several alternatives in the market to solve the same problem, different algorithms, side-effects from coding and designing, and more. Building software requires extreme detail orientation to cover given requirements and to avoid undesired bugs.

Since Software Engineering is complex, it is important to give some steps back and design before acting. Technical Designs are like blueprints that we create to build more robust applications.

Below there are some benefits from this kind of document.

## Structured ideas

Documents provide the place to decode ideas into structured blocks with headings, paragraphs, and sentences in a way that any person, living in any place, at any time, can understand and make their conclusions and comments about different topics in a few minutes.

It is easier to understand and follow a structured idea for a complex task in a document than in a meeting.

## Clear comparison of trade-offs

> "Everything in software architecture is a trade-off. First Law of Software Architecture" - Richards, Mark; Ford, Neal. Fundamentals of Software Architecture

There are multiple ways to solve the same problem. There are thousands of libraries to achieve the same goal. What is the best approach for the given problem? It depends.

What works for project A may not work for project B. The technology for your team may not be perfect for another team. Everything in Software Engineering has trade-offs!

It is important that Engineers understand this first law of Software Architecture as soon as possible. It's valuable when we learn:

- To see different approaches
- To identify the cons of our approaches

Most engineers do not know to think to alternatives, they are driven by speed and they completely take the first idea as the best one. Most of time, this cause side-effects, undesired bugs ane make the software harder to maintain and extend.

Right after learning to think about alternatives, the engineer must learn to identify the cons of approaches. Seeing only good aspect from ideas can be dangerous. Everything has trade-offs!

The engineer is required to think about approaches and their trade-offs when they separate time to design before the implementation. Comparing approaches at this moment is easier because the Engineer is working in a high level phase, in a human language instead of a computer language. There is no energy wasted to encode/decode information to a computer language. The engineer can focus resources entirely to find the best approach for the given dilemma.

## Clear communication

Designing before implementing gives the chance to be synchronized with the team. The team can interact, collaborate and stress the solution in documents to avoid misunderstandings and issues throughout development.

Taking important architectural decisions on documents is cheaper than on coding. Reverting a document in a human language (higher language) it is cheaper than reverting an architectural decision on code (lower language).

A big result of implementing Technical Designs is having fewer big refactors on PRs, for example. The team had the opportunity to:

- Design the solution
- Interact through documents
- Define the best approach
- Refactor the design instead of coding
- Agree on the final solution

The final code on PRs will be more assertive since the team had the opportunity to cooperate previously on desiging section.

## Time saver

Technical Designs are time savers. Interacting on documents gives the chance to:

- Reduce the amount of meetings
- Having async communication instead of sync communication

This kind of document can easily replace a meeting and it makes the team more productive. This document can be understood in a few minutes because the idea is well structured. On other hand, sharing designs verbally in a meeting can consume more time since the verbal communication may not be as refined as writing communication. It is harder to people visualize the solution verbally. Remember that software engineering is not easy!

Finally, this document provides the chance to work asynchronously. It is possible to read it, make observations, and approved it whenever is possible. Asynchrnous tasks provide time flexibility for collaborators.

## Faster development

The hardest part of designing solutions without Technical Designs is to take decisions meanwhile encoding ideas to a computer language. Designing meanwhile you are coding is a performance drainer.

There are different aspects to think in the designing phase like open questions, compare alternatives, cover all requirements, pay attention to edge scenarios and more. Designing meanwhile we enconde/decode everything to a computer language just adds another complexity layer in a topic that is already complex.

Separating concerns is the best answer. Let's separate development into two phases:

- Designing
- Implemeting

Clear designs empower engineers to code faster.

## Reference for design decisions

Often, Engineers ask themselves about the taken design decisions. In this case, Technical Design documents can be used as reference for this kind of question.

Technical Designs will be great resources whenever Engineers feel unconfortable with previous decisions. It will be possible to understand the problems and thoughts at the moment the decision was taken.

## Faster onboarding

Onboarding new Engineers to a project is challenging and Technical Designs can be powerful to help in this aspect.

New Engineers can separate two days to read previous Technical Designs. Those documents will provide a clear vision about the software, in a human language level. All of this new information will be easier to digest and gives the confidence to the new member start to collaborate sooner.

## Extreme quality

Fast development is not enough. What is the value building something really fast ignoring good principles? There are a lot of principles in Software Engineering to make the solution more readable (Clean Code), more extendable (SOLID), simple (KISS) and efficient (DRY and YAGNI).

Designing before implementing delivers more time to put thoughts on topics that really matter. The Engineer can think more about architectural aspects like:

- Scalability
- Performance
- Security
- Extendability
- Auditability
- Readability
- Requirements
- Data Structures
- Testability
- Edge cases

# Creating a Technical Design

## Background

## Objectives

## Design

## Approaches

## Open Questions

## Should we provide an example?

I'm not sure if we can create an example on Notion and share it.

Suggestion:

- Wordle API
- Wordle UI

# Tips for writing Technical Design documents

## Use headings

## Be consistent

- Be consistent on your structure on all TD docs

## Do not write a Technical Design for simpler problems

- Avoid to create Technical Design for simpler problems

## You won't be slower!

## Improve your writing skills

## Design right after understanding completely the given requirements
