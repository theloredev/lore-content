---
id: automated-testing
title: Automated Testing
sidebar_label: Automated Testing
---

## User Acceptance Testing (UAT)

Let's discuss the importance and best approaches to User Acceptance Testing or UAT. 

"UAT is important because it helps demonstrate that required business functions are operating in a manner suited to real-world circumstances and usage. If the expected outcome is not achieved during testing, the item will be documented and sent back to the developers for repair." <a href="https://www2.stardust-testing.com/en/the-value-of-user-acceptance-testing#:~:text=The%20Importance%20of%20UAT,to%20the%20developers%20for%20repair." target="_blank">StarDust</a>  

User Acceptance Testing may be a contractual requirement that allows the customer or sponsor of your application to verify the software delivers all requirements and features and will meet the needs and expectations of the end-users of your application. 

For this section, we will discuss the two most common approaches to User Acceptance Testing, Waterfall and Agile, and explore both methods' benefits and risks.

Whether you select a Waterfall or Agile approach for your User Acceptance Testing efforts, you should always seek to involve the assistance of a Quality Assurance tester or a Business Analyst. A Business Analyst or Quality Assurance tester can help capture any changes or modifications to requirements or any software shortcomings noted by customers or end-users.

Besides, both the Waterfall and Agile User Acceptance approaches may create situations where you receive conflicting requests for software modifications or requirements changes, mainly if the testing includes multiple customers or end-users. 

For example, you could conduct a user acceptance test session in which some end users request all GUI screens to be blue, while another group of users or customers demands all screens to be green. Who decides the final modification?

For this reason, it is best to know ahead of time who is the designated decision-maker. In the event user acceptance testing results in requests from conflicting software modifications, the designated decision-maker will determine the final requirements changes. 

### Waterfall User Acceptance Testing

The Waterfall software development methodology is one of the oldest and most well-known approaches in the development community.  All development phases are completed in sequence, with the next phase only beginning when the current phase has been completed. 

In the Waterfall approach, User Acceptance Testing occurs toward the very end of the software development lifecycle during the Testing phase, sometimes called the Verification phase,  pictured below:

![](assets/testing/automated-testing/waterfall-model.png)

<a href="https://airbrake.io/blog/sdlc/waterfall-model" target="_blank">Waterfall Model: What Is It and When Should You Use It?</a>  

- Some scenarios in which a Waterfall approach to User Acceptance Testing may be appropriate include:
 
    - Development of a system or application in which the team has a high degree of certainty that the requirements will not change during the project
 
    - Development of a small system or application that that will have a relatively short project duration
 
    - When your system or application is a large project requiring "the stringent stages and deadlines available within these cool, cascading waters" Waterfall Model: What Is It and When Should You Use It?
 
    - When you are developing a system or application for an organization requiring rigorous, formal, or heavily structured development processes or security protocols

- Some benefits of a Waterfall approach to User Acceptance Testing include:
 
    - The ability to provide your customers or end-users with clear and established deadlines and milestones
 
    - A linear development approach easily understood by most developers and customers
 
    - All known customer requirements are gathered and readily available before software development begins.
 
    - Less customer involvement required during the life cycle, which may be appealing to customers with limited time availability

- Some risks of a Waterfall approach to User Acceptance Testing include:
 
    - A Waterfall User Acceptance Testing approach is of little value for software development projects when a full set of a clear set of requirements is not available before the Development phase of the life cycle. 
 
    - The Waterfall approach to User Acceptance Testing increases the risk of "bugs and vulnerabilities as the testing process starts only when the project development is over" Agile vs. Waterfall: Differences You Should Know
 
    - Requirements changes during a long-term software development project cannot be accommodated after the Waterfall lifecycle's Requirements phase.
 
        - There is a risk that User Acceptance Testing occurring late in the life cycle results in the application being deemed abandoned Shelfware: "Computers. software or hardware that remains unsold, unused, or underused:" Dictionary.com
 
        - Major changes to laws, regulations, and market conditions impacting the application may occur during the lifecycle development phase.  The final application may be determined during User Acceptance Testing to no longer be useful, viable, or aligned with the customer's current needs. 
 
        - Additional costs associated with requirements and development rework if User Acceptance Testing determines the final application does not meet all requirements but can be salvaged through repair and modification
 
        - As an example, imagine your team is developing software for processing Income Taxes. 
            - Major changes to tax code law occur during your software development phase.
            - During User Acceptance Testing, the customer may determine your application does not meet their needs.
                - The customer may decide your application is not ready for release, resulting in major rework of the application or possible cancellation of the project. 

### Waterfall Acceptance Testing versus Agile User Acceptance Testing 

- Using the Waterfall approach, User Acceptance Testing only occurs toward the end of the development life cycle.
 
- In the Agile approach to User Acceptance Testing, modules and portions of the application are reviewed and verified repeatedly by the customer, business owner, or end-users throughout the development life cycle.

![](assets/testing/automated-testing/waterfall-vs-agile.jpeg)

<a href="https://hackr.io/blog/agile-vs-waterfall" target="_blank">Agile vs. Waterfall: Differences You Should Know</a>   

### Agile User Acceptance Testing
 
Agile User Acceptance Testing is a newer, more flexible approach to receiving customer feedback and verifying software modules and products. Using the Agile approach, modules, or portions of the application, are offered to the customer for review repeatedly throughout the entire development life cycle. 

Agile approaches to User Acceptance Testing have been widely embraced and favored over the Waterfall approaches in the software development community due to the increasing size and complexity of software applications and rapid changes in requirements and technological demands. 

- Some scenarios in which an Agile approach to User Acceptance Testing may be appropriate include:
 
    - Software applications for which all requirements are not known before the start of development
 
    - Software applications where there is an expectation that requirements and customer needs may change and evolve throughout the development process
 
    - Development projects where the customer or end-users wish to see incremental progress and maintain continued involvement throughout the software development life cycle
 
        - Due to its iterative nature, Agile User Acceptance Testing allows customers and end-users to maintain a continuous feedback loop throughout the software application's development and evolution. 
 
    - Development efforts where there is a need to limit the cost and time of rework caused by delivery of a final product that is not well-aligned with customer needs and expectations

Let's take a brief look at how an Agile approach to User Acceptance Testing might be used on a development project using an agile approach, such as Scrum: 
 
![](assets/testing/automated-testing/agile-sprint.jpg)

<a href="https://www.sciencedirect.com/science/article/pii/S016412121730002X" target="_blank">User acceptance testing for Agile-developed web-based applications</a>  

- As we can see, unlike the Waterfall approach, the Agile approach to User Acceptance Testing allows for continuous, iterative feedback and revisions by the customer and end-users.
    - The customer/end-user reviews every software module or component proposed for release.
    - This approach increases the likelihood that the final, full software product will meet customer requirements and expectations. 

The agile approach allows customers and end-users to inform the development team of any changes to requirements or new requirements that need to be incorporated into the system to ensure the final software application is viable and aligned with the latest requirements and expectations. 

- Some benefits of using an Agile approach to User Acceptance Testing include:
 
    - The ability to begin software development efforts when all requirements may not be known at the beginning of the development life cycle
 
    - The ability to  accommodate and incorporate significant changes to customer requirements, customer expectations, laws, regulations, and market conditions throughout the development life cycle
 
    - A deeper understanding of the software requirements by the development team through continued feedback from customers and end-users
 
    - Continued involvement by customers and end-users inspires a sense of "ownership" of the application being developed, increasing the likelihood the end product will be accepted and embraced by the customer and end-users
 
    - "Reduced risk of failure as the process is completely based on incremental progress" Agile vs. Waterfall: Differences You Should Know
 
    - Reduced cost risks associated with major rework that could be required if User Acceptance Testing was conducted only toward the end of the development life cycle

- Some risks of using an Agile approach to User Acceptance Testing include:
 
    - The possibility that User Acceptance Testing may result in the request for new requirements or features well outside the scope of the original development project:
 
        - It is not uncommon for Agile User Acceptance Testing to lead to customers or end-users requesting new features that require significant changes to the software development project's original scope.
 
        - If newly-introduced requirements deviate significantly from the original scope of the application, the project itself could be derailed. An agile approach adds a "heightened risk of project derailment." [Agile vs. Waterfall: Differences You Should Know.](https://hackr.io/blog/agile-vs-waterfall)

    - Unknown deadline for completion of the overall application:
        - Since an agile approach allows for multiple user acceptance tests, customer reviews, and modifications, each iteration extends the timeline for the application's overall completion.  As a result, the application's completion date is always considered a "moving target" and subject to change.

    - Limited customer, business owner, or end-user availability:
 
        - The development efforts can be significantly slowed if customers or end users are not readily available to participate in interactive User Acceptance Testing and provide the necessary feedback loop to promote further development and refinement of software modules.
            - In this sense, the customers, sponsors, business owners, or end-users needed for User Acceptance Testing can become roadblocks to complete the application.
    
    - For short-duration projects (under two weeks),  where quick delivery is expected, an agile approach to User Acceptance Testing could considerably delay the software application's completion. Agile is considered not "suitable for small-scale projects" <a href="https://hackr.io/blog/agile-vs-waterfall" target="_blank">Agile vs. Waterfall: Differences You Should Know.</a>  

For most medium to large-scale modern software or application development efforts where requirements, expectations, and demands may evolve rapidly, an Agile approach to User Acceptance Testing will likely prove a better fit than the older Waterfall approach. 

### Types of User Acceptance Testing: Methods Available 

Let's look at some of the methods available for conducting User Acceptance Testing, whether you have chosen a Waterfall or Agile approach to testing.

- Alpha Testing
    - Most suitable if an Agile User Acceptance Testing approach has been chosen. Alpha Testing involves allowing a small, select group of users to test-drive specific software modules and system features during their earliest development stages.  
 
        - Due to the instability of the application at this stage, the small test group would likely include only the customer, sponsor, or business owner, along with a hand-selected group of technology-savvy end users likely to understand and tolerate early-stage software bugs.
 
        - This type of testing is widespread in the video game software industry but has gained increasing popularity throughout the entire software development community.

- Beta Testing
    - Beta testing involves allowing a small to medium-sized group of select users to test-drive a software system or modules near completion.
 
        - Due to the instability of the application at this stage, the small test group would likely include only the customer, sponsor, or business owner, along with a hand-selected group of technology-savvy end users likely to understand and tolerant of moderate software bugs and willing to provide constructive feedback. 
 
        - This type of testing was first widely-adopted by the video gaming industry but has gained increasing popularity throughout the entire software development community in recent years.

- Early Release or Pilot Programs
    - This approach to User Acceptance Testing involves creating an isolated, near-Production quality replica of the software or application.
        - A small, carefully selected group of test users is given early access to the application.
        - The test users begin using the application to perform their normal business functions to evaluate the application's quality, performance, and viability for long-term usage by a larger group of users.

- Contract Acceptance Testing
    - Contract Acceptance Testing typically involves one or more formal meetings with the customers or end-users. The application is reviewed in real-time for compliance with a "checklist" of requirements stated in a contract that funds the software development efforts.
 
        - For example, government contracts frequently include a Statement of Work with an itemized list of software requirements that can be used as a "checklist" during Contract Acceptance Testing.

- Regulation Acceptance Testing
    - This form of User Acceptance Testing involves validation by a subject matter expert to ensure the application or system complies with applicable regulations and laws. 
 
        - For example, a software application developed for the telecommunications industry may be reviewed by an experienced engineer to ensure compliance with Federal Communications Commissions (FCC) regulations. 
 
        - "Regulation Acceptance Testing, also known as Compliance Acceptance Testing, examines whether the software complies with the regulations. This includes governmental and legal regulations." <a href="https://usersnap.com/blog/types-user-acceptance-tests-frameworks/" target="_blank">5 Types Of User Acceptance Testing</a>  

- Operational Acceptance Testing

    - This form of User Acceptance Testing is normally conducted as manual testing by the sponsor, customer, or other subject matter expert with expertise in the organization's business processes. 
 
    - This type of testing aims for the customer or end-users to verify that your application or system conforms to their current business processes and workflows. 
 
    - Ordinarily, this type of testing entails having customers or end users attempting to manually use your application or system to complete routine business tasks the software was developed to facilitate. 

### References

- ""5 Types Of User Acceptance Testing" <a href="https://usersnap.com/blog/types-user-acceptance-tests-frameworks/ " target="_blank">https://usersnap.com/blog/types-user-acceptance-tests-frameworks/</a>
 
- "Agile vs Waterfall: Differences You Should Know" <a href="https://hackr.io/blog/agile-vs-waterfall " target="_blank">https://hackr.io/blog/agile-vs-waterfall </a>
 
- "User acceptance testing for Agile-developed web-based applications" <a href="https://www.sciencedirect.com/science/article/pii/S016412121730002X 
" target="_blank">https://www.sciencedirect.com/science/article/pii/S016412121730002X</a>

- "The importance of UAT" <a href="https://www2.stardust-testing.com/en/the-value-of-user-acceptance-testing#:~:text=The%20Importance%20of%20UAT,to%20the%20developers%20for%20repair." target="_blank">https://www2.stardust-testing.com/en/the-value-of-user-acceptance-testing#:~:text=The%20Importance%20of%20UAT,to%20the%20developers%20for%20repair.</a>
 
- "Shelfware" <a href="https://www.dictionary.com/browse/shelfware" target="_blank">https://www.dictionary.com/browse/shelfware</a>





