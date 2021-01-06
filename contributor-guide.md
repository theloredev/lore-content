---
id: contributor-guide
title: Contributor Guide
sidebar_label: Contributor Guide
---

## What is Lore? 

Lore is an open-source guide of best practices, techniques, and standards. It's written by developers, for developers of all technologies. The knowledge found within this guide is applied abstractly for individuals across a broad array of contexts. This document aims to make the process of contributing clear and answer questions you may have. 

## Code of Conduct 
Lore has adopted the Contributor Covenant as its Code of Conduct, and we expect project participants to adhere to it. Please read the full text so that you can understand what actions will and will not be tolerated.

## Terminology and Notes 
This guide uses RFC 2119 terminology when using key words like "must", "must not", "shall", "shall not", "should", "should not", "may".

## Open Development 

All work on Lore happens directly on GitHub. Both core team members and external contributors send pull requests, which go through the same review process.

## How to Contribute? 

We welcome the entire community to share their knowledge. However, there are a few guidelines to keep the information aligned with the overall vision. 

What you should write about:
- Best practices
- Battle-tested Techniques
- Standards and Conventions
- Principals and fundamentals of software engineering

What you should not write about:
- Introductory overviews of technologies (What is React, etc.)
- Non-battle tested opinions

To help make your contributions better, we have some guidelines.
- Provide focused and detailed information about the topic
- Provide graphics and illustrations if applicable
- Provide real-world examples
- Provide references, and use more than just Wikipedia
- Use concise language and tone (straightforward and simple)
- Write in small paragraphs [(users don't read, they scan)](https://www.nngroup.com/articles/how-users-read-on-the-web/)
- Don't ask questions. Make statements.
- Add quotes from a well-known expert. 
- Avoid saying what you are going to say; instead, just say it. For example:
    - "In this section, we will."
    - "This chapter, we will cover." 
    - "Let's start by saying"  

## Use short sentences and subheading:

Write in small paragraphs (users don't read, they scan)

Break the paragraphs into short sentences. It helps our reader scan the book, which is how users usually consume content on the internet by scanning the information and not reading all the text.

### For example:

#### How it was

"Unfortunately, cybersecurity risks and attack strategies have become overwhelmingly coordinated and synchronized to a point where new advancements in data, software, and hardware actually generate more loopholes and open patch risks for hackers and cybercriminals to exploit."

#### How it turned to be: 

"Unfortunately, cybersecurity risks and attack strategies have become overwhelmingly coordinated and synchronized.

In such a way to a point where new advancements in data, software, and hardware actually generate more loopholes and open patch risks for hackers and cybercriminals to exploit."

## Bullet points: 

When there's an opportunity, let the information in the form of a bullet list or numbered list. For example:

### How it was: 
"Management teams are tasked with planning, organizing, monitoring, evaluating, implementing, and staffing with the end goal of strategically moving their company forward."

### How it turned to be: 

"Management teams are tasked with:
- Planning
- Organizing
- Monitoring
- Evaluating
- Implementing and
- Staffing with the end goal of strategically moving their company forward."

## Your First Pull Request 

### Commits for new files should follow the terminology below:  

#### Branch: 

feat/Category/Topic  

#### Commit message: 

feat('Category'/'Topic'): so 'topic' is published under 'Category'   

#### Filename  
topic.md  

### Example: 

I'm currently writing about the topic of Communication that falls under the Core Skills category.

### filename: 

[communication.md](https://github.com/theloredev/lore-content/blob/staging/core-skills/communication.md)  

### metadata:  

```
---
id: communication
title: Communication
sidebar_label: Communication
---
```

### Step-by-step: 

1. Branch feat/Category/Topic
    - (e.g. git checkout -b feat/CoreSkills/Communication)
2. Commit message feat(Category/Topic) so topic is under Category
    - (e.g. git commit -m 'feat(CoreSkills/Communication): so communication is published under Core Skills)
3. Push to the official repo 
    - git push origin feat/CoreSkills/Communication
4. Open your Pull request :)   


# Conventional Commits  

Lore's contributions follow the conventional commits. For full documentation on their naming structure please refer to their [website](https://www.conventionalcommits.org/en/v1.0.0/). 