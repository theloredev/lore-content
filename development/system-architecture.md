---
title: System Architecture
sidebar_label: System Architecture
---

> "Architecture is about the important stuff. Whatever that is" - Ralph Johnson

Every developer loves working in systems that are easy to maintain, but those kinds of systems just don’t happen by accident. A great deal of planning and forethought has taken place in order to construct a complex system that is considered to be well architected.

So what is System Architecture? As Ralph Johnson put it, it is the “important stuff.” The IEEE weighed in and created a standard known as IEEE 1471, which states:

> "Architecture is the fundamental organization of a system embodied in its components, their relationships to each other, and to the environment, and the principles guiding its design and evolution."

The standard goes even deeper into defining the various aspects of the above definition, but some key aspects of system architecture are:

- A set of significant decisions
- The structural elements
- The architectural style
- Relationships between elements
- The behavior

And takes into consideration:

- The environment
- The stakeholders
- The mission/purpose

## Oh why bother?

Every client wants to see a team of developers instantly grab their requirements, lock themselves in dark rooms, and begin to furiously type to create an application that meets their needs. While we know that isn't how things work, our clients may not. It is imperative that clients understand that taking the time to properly architect a solution will pay for itself.

The short term gains of immediately trying to implement various pieces of functionality are very quickly overtaken by the benefits of properly building the system's architecture. Using the chart below, the system that is well thought out has a few weeks of slower progress, but after those weeks, the higher quality of the resulting code pays dividends with a more reliable, stable, and enhanceable system over time.

| ![](assets/development/system-architecture/quality-over-time.png) |
|:--:|
| *Credit: <https://martinfowler.com/articles/is-quality-worth-cost.html>* |

With this higher quality software, there happen to be a number of positive side effects. The software is:

- Easier to change and enhance
- Easier to understand
- Less likely to contain errors and bugs
- Easier to test

## Some Principles and Best Practices to Follow

- Keep initial design work to a minimum: this may seem counter to what was stated in the previous section, but it makes sense when you think about it, especially if you work using Agile methodologies. Putting together an initial high-level design, and then focusing in on some smaller chunks so those pieces can be worked by developers is significantly more important than creating one of those really spectacular graphics with lines pointing at different systems.
- Keep it simple: Keep your system as simple as you possibly can. Unnecessary complexity to solve problems the system will likely never face is a waste of resources during initial development, and a continued waste as developers continue to work in this system for years to come.
- Single Responsibility Principle: Each module or section of your system and application should be concerned with solving a single problem. For example, if you are using an MVC architecture, each controller should handle (or control) a single section of the application.
- Scalability: How will your system grow and expand over time? Making the right architecture decisions upfront can save you some major headaches down the road. For example, utilizing Horizontal Scaling (adding more servers) rather than Vertical Scaling (adding more hardware to an existing server) can lend itself to more scalable systems. Leveraging cloud based platforms lend themselves quite well to Horizontal Scaling.
- Self Healing/Crash Resistant: Stability of a software system is vital. One way to ensure a system is stable is to take into account how faults and exceptions will be handled by the system.
    - Error Logging: Logging within a system should be carefully designed to maintain a balance of logging important information, but not over-logging and polluting the logs with unnecessary data. Most (if not all) modern programming languages have libraries to easily facilitate and manage the logging and support for various logging levels.
    - No Single Point-of-Failure: Redundancy can and should be built into systems so no single part of an application can bring down the entirety of an application. For example, systems can use load balancers to ensure an even spread of users across a pool of servers. The load balancer can also incorporate failover support so if the application goes down on one server, it will simply be taken out of rotation.
- Reuse rather than re-implement: The specific implementation that solves a specific requirement should only be implemented in one place within an application. You shouldn’t need to implement the same solution in more than one place.
- Responsiveness: A system should take into account performance, and time should be spent tuning a system for maximum throughput. This architecture task can often take place later in the development process as, “Premature optimization is the root of all evil” -- Donald Knuth.
- Separation of Concerns (Soc): Each part of your application should be divided into distinct sections, and address a specific piece of functionality.
- Secure: It is important that the architecture for a system incorporates current security standards, such as PCI Compliance for commerce systems, and the encryption of passwords and other sensitive data stored in databases.
- Law of Demeter: Each object and each section of an application should have limited knowledge of other objects/sections of the application. Failure to do this can result in a tangled mess of code and systems.
- Analytics Considerations: The value of analytics, especially for web applications, has rapidly increased in recent years, leading to many applications needing to shoehorn analytics and the ability to do A/B testing into applications that weren’t necessarily designed to support it. New systems should be built with analytics in mind.
- Automate What You Can: This can be as simple as incorporating continuous integration, to using automated testing tools to regression test your application, to going as far as to use newer AI technologies to auto-generate portions of code.
