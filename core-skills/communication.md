---
id: communication
title: Communication
sidebar_label: Communication
---

A big part of our day to day work is about communicating effectively with others. This is extremely important because the overall process of building a product requires harmony between people and a clear understanding of everyone’s role in what’s being built.

Here are some reasons why effective communication is important:

- Building great software is hard 
- It avoids confusion
- It provides purpose
- It creates accountability
- It saves time and eventually money 
- It builds trust 

Oftentimes, engineers focus only on learning about new technologies and neglect improving their ability to communicate with their co-workers. Achieving the proper balance between technical ability and strong communication skills is the difference between a good developer and a great one. 

## Communicating Issues To Teammates

While working through tasks, there will inevitably come a time where you run into an issue that becomes a blocker. These issues can come from many different places, such as an API not matching its documentation, or getting stuck working out some complex logic. When you find yourself in a situation like this, after you have done your due diligence to seek a solution on your own, reaching out to your teammates becomes your new top priority.

There are several benefits to reaching out to your teammates, including:
- Other developers may have run into this issue before and have a solution
- A fresh pair of eyes may see your problem from a new light and offer an alternative solution you didn’t think of
- Your teammates are kept informed of your status on your task, and this setback can be planned for accordingly
- Can boost a team’s collaboration and teamwork proficiency
- When your teammates come together and solve an issue, there is an increase in the team’s collective knowledge

Every developer runs into blockers, but great developers humble themselves, and seek help from their colleagues in order to overcome challenging issues.

## Communicating Bugs

As engineers, we occasionally will run into bugs while trying to develop solutions to our assigned tasks. These bugs should not be ignored, but instead, be communicated to your team and project manager via agreed upon communication tools, such as email, instant messaging, etc.

You should also begin the process of  clearly documenting the bug by, at the very least, providing the following information:
- The expected behaviour/result, and what is really happening
- All of the steps needed to reproduce it, including things like the OS and browser used
- The impact of the issue to your current development task
- Possible solutions with their relation between cost vs. benefit

This well documented bug can then be added to whatever tracking tool your team/organization is using (e.g. Trello, Github, Jira, Google doc).

## Communicating Task Delivery Delays 

If there's going to be a delay when delivering a task, let your project manager know as soon as possible. Do not wait until the due date to reveal the delay. As soon as you know you're going to be late, figure out why, what you're going to do to prevent that from happening in the future, as well as the new due date. Additionally, you should seek out ways to reduce the impact of the delay, such as adding staff, using different tools, or adding hardware, and present your ideas to the project manager. 

For example, if you are working with a team that has weekly sprint meetings every Monday to set the tasks you will be working during the week, don’t wait until Thursday or Friday to communicate to your team that you won’t complete your task. Again, you should communicate with them as soon as you know that you won’t be able to deliver the task; then provide the best information you can about the cause of the delay, the expected impact, the probability it will occur, your thoughts about mitigating it, and your worries concerning it. 

## Communicating Changes

Be transparent about any changes related to how you go about completing certain tasks if they have the potential of affecting aspects of the codebase that others worked on. For example, an integration or some aspect of the product’s architecture. Before changing components of a system that could have a broad impact, make sure that you let others know about the changes, their potential impact, and why you need to make these changes. This will give others the opportunity to provide feedback, provide alternative solutions, and to ensure that this is the right time to make these potentially major changes. 

There is a great deal of risk associated with making big changes to an application. It is very easy for these changes to introduce bugs into the system, and cause unexpected areas of the application to break. To reduce the risk, [Unit Tests](testing/example.md) can be created to mitigate some of that risk.

Some examples of when should I communicate changes:
- When the scope of a task needs to be modified
- When the approach or methodology to complete a task is changing
- When I’m going to delay a task I’m working on 
- When I am working on a part of the product that affects many components (Ex. If you change an API or some aspect of the codebase’s architecture) 

## Communicating Updates

Over the course of both projects and individual tasks, it is extremely important that other team members are aware of what you are working on. These team members may be other developers, testers, project managers, project owners, or really anyone with direct interest in the status of the project.

When should I provide updates:  
- When taking ownership or starting a task
- When I finish a task earlier than I expected 
- For larger tasks, providing a daily update with an estimated “percentage completed”
- [When I’m stuck on something I’m doing](#communicating-issues-to-teammates), and I see that there’s a potential delay
- When I need to run a build or deployment to an environment
- When I complete a task and my changes are ready for [code review](#code-review)
- When in a leadership or decision making role for a team, and a previous decision needs to be changed, such as a change to an API your development team is relying on
- When your availability is changing, including:
    - Short term changes: a doctor appointment in the afternoon or taking a Friday off
    - Long term changes: a leave of absence or vacation 
    - Scheduling changes: splitting time with a separate client

## Asking Questions

One of the greatest skills an engineer can have is the ability to ask good questions. It shows that you have humility, that you care, and are truly interested in delivering a successful product to the client. 

### Asking Clarifying Questions 

When there is a lack of clarity with requirements, it is important not to make assumptions. If you are not sure that what you are building will 100% fulfill the requirements of the task, then don’t be afraid to ask. Great developers build with the end goal in mind and ask questions about requirements when it is not clear to them.

For example, your project manager or product manager comes up with a new feature that they want to add in the next sprint. In the requirements, they specify [third-party integrations](https://gbksoft.com/blog/third-party-integration/) and tools you should use. Be sure to ask clarifying questions on why they made those choices. If you have a better solution, then you should tell them. Great engineers ask questions and provide their own feedback in a constructive way. 

You could encounter a situation where you receive design files from a designer but have an alternative solution in mind for building a particular screen that takes into consideration certain factors the designer wasn’t aware of, such as performance or ease of use. Do not be afraid to bring up your thoughts, questions, or concerns to designers or project managers when it comes to the UI/UX of a feature or the project as a whole.

Ask questions when: 
- You are not 100% sure about the task or a feature you will build  
- If you don’t agree with the requirements and have better suggestions 
- When requirements between two different tasks are contradictory
- When the timeline or deadline doesn’t seem achievable
- If you aren’t sure you have sufficient resources (people, tools, equipment) to complete a task

## Communication Tools

There are quite a few different tools that can be utilized to communicate with other team members, as well as with clients. Knowing which communication tool will work best in different situations is as important as knowing which IDE works best with different programming languages. Each tool comes with its own advantages and disadvantages, which can aid you in making an informed decision on which tool to use.

### Email

The old standard! Email revolutionized both the way people communicated at work and the speed with which they could communicate.  With this in mind, here are some best practices and recommendations on when and how to communicate via email.

When to use:
- When you don’t need an immediate answer. Email is asynchronous, so the expectation is that you will get a response in the near future.
- When you are asking a more complex question and need a more detailed answer.
- When you wish to provide some detailed information.
- When you want to begin a dialog with multiple people.
- When communicating with a client outside of your organization who may not have access to some of your other forms of communication.
- When seeking an official decision that could be problematic later on.

What not to do:
- CC people that aren’t going to provide any value to the conversation.
- Email signatures with big, goofy images in them (employer required signatures being the exception).
- Don’t send a follow-up too quickly. Take the time to provide a clear, concise, and accurate response.

Advantages:
- Easily searchable
- Archive of project information (assuming your email account remains active, and deleted emails are archived and not purged)
- Universal - Everyone has email!

Disadvantages:
- Slow response time
- Emails can be lost. People may get hundreds in a day and may miss the email you sent.
    - If you need to ensure your email gets noticed, consider requiring a return receipt, so you will be notified when someone reads your email.
- Spam - Your email can sometimes get flagged incorrectly, which is incredibly frustrating.

### Chat/Instant Message Tools

Instant Messaging tools have been around for a while. ICQ and AOL Instant Messenger paved the way for a number of services used throughout the industry today. There are several newer tools that have been designed specifically for business, such as Slack and Microsoft Teams, and a host of other tools that support instant messaging, such as Skype, WeChat, Google Hangouts, etc. 

When to use:
- When you need a quick response
- When you want to post a question to a group of people (depending on service)
- When you want to begin a conversation among a group of people.

What not to do:
- Don’t start a conversation with “hello” and then say nothing until you get a response.
- Don’t send
    - A bunch
    - Of short
    - Messages.

Advantages:
- Quick
- Archivable and searchable (depending on the service)
- Informal
- Great for team communication (depending on the service).
- Some support connectivity with external services (like github, Jira, Trello, etc).
- Many support voice and screen sharing functionality.

Disadvantages:
- Potentially distracting
- Depending on the service, a subscription may be required to access all features.

### Audio/Video Conferencing
An exceptionally common way for people to carry out meetings, especially when participants are spread across numerous locations.
Video conferencing services have been around for quite a while, and using them has become pretty common in many organizations.

When to use:
- Great for remote team meetings and customer meetings. 
- Anytime you need to gather people together 
- When decisions need to be made and issues need to be discussed.
- When seeking multiple opinions on how to resolve an issue.

Advantages:
- Many services support both audio and video conferencing.
- Remote team members are able to join and contribute.
- Many support screen sharing.
- Users typically just need a phone to connect.
- People can be away from their computers and still join.
- People are very familiar with meeting this way.

 Disadvantages:
- Requires a pretty solid internet connection for video.
- Prone to disruptions when members are connecting from home (pets, children, traffic, construction, etc).
- Shy individuals may not speak up during the call.

## Meeting 

Meetings can be a great way to connect with your team members, but they must also have a purpose that makes the time spent worthwhile. 

Basic rules that you should follow: 

- When calling a meeting, have an agenda and stick to it
- When leading a meeting, spend time beforehand preparing what you’ll be saying or presenting
- Be on time
- Be presentable
- While in a meeting, wait until someone finishes speaking before talking
- Ask questions if you have them.
- Pay attention to what others are saying 
- Make sure everything is working, audio, microphone, and your internet 
- Be respectful 

### Sprint Planning

If your team is using Agile, Sprint Planning meetings provide structure, set expectations and define the backlog for upcoming sprints. Engineering teams utilize sprint planning to better organize and ensure the success of the sprint. This meeting occurs once per sprint, and is used to address action items, roadblocks, and questions for the upcoming sprints and to seek resolution to blockers from the current or past sprints.

### Stand-up 

If your team is using an Agile approach, you will have to participate in daily Stand-up meetings. Stand-ups should be short (no more than 15 minutes) and highly focused meetings where developers provide their status on their current task(s). The idea behind the “Stand Up” is that no one wants to stand for all that long, so the quicker everyone gets through their list, the quicker everyone can sit back down.  

Questions to answer during the stand-up

- What have you worked on since the last Stand-Up?
- What are you currently working on?
- What will you be working on next (before the next Stand-Up)?
- Is there anything blocking you from completing your task (Optional) 
- Request any additional support for your current task (Optional)
    - Request time with another attendee after the stand-up completes or at a specified time during the day. Do not hijack the Stand-Up.

