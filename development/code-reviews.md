# Background

Code Review is an important software quality assurance activity. In Code Reviews, the code’s author requests reviews from other Engineers to ensure that the given source code follows the expected quality to be deployed. The first well-known Code Review Process was called the [Fagan inspection](https://www.professionalqa.com/fagan-inspection) created by Michael Fagan.

Trio has its own Code Review Guideline to identify code quality. Trio is a very technical company and we must ensure that our engineers are able to provide excellent code reviews in external and internal projects.

# Benefits from Code Reviews

Reviewing code is an essential step to ensure code quality. The lack of code quality compromises development performance over time. Complex code is harder to maintain and adapt. As Robert C. Martin says:

> “So if you want to go fast, if you want to get done quickly, if you want your code to be easy to write, make it easy to read”

To go faster we should go well. The speed should not compromise the quality. Code Review is an important tool in Software Engineering, skipping it or performing bad Code Reviews could bring critical damages to the codebase, the client and the company.

Some benefits from good Code Reviews are:

- We are able to make the codebase easier to understand, follow, adapt, maintain and extend
- A good line of code encourages the Engineers to keep writing more good lines of code
- We are more likely to catch errors or side-effects before deployment
- It provides clear feedback for Engineers
- It spreads technical knowledge through the Engineering team
- It keeps the Engineering team on the same page

# Reviewing Code

Code Reviewing is a task that demands attention in several areas. Let’s see them!

## Code Legibility

Good code is easy to understand and change. Following there are some important aspects regarding Code Legibility with some examples.

### Meaningful names on variables, methods, and classes

Software Engineers truly care about naming the components with clarity and objectiveness. The name from a variable, method, or class should avoid any extra effort of explanation or comments because the name already should explain itself.

Imagine we have a Slack bot that sends a nice _welcome message_ to new users. This message says `If you have any problems please reach @Person`. We need a properly named environment variable to mark this person in the message:

```jsx
// BAD
ADMIN_WORKSPACE_ID = 1234;

// GOOD
SLACK_USER_ID_TO_NOTIFY_HELP_MESSAGES = 1234;
```

By reading the bad example, we might infer that the `ADMIN_WORKSPACE_ID` variable has a big responsibility. It could bring the wrong idea that it does much more than just tagging a person in a message. This variable name brings more questions than answers. We won’t feel comfortable changing it and will very likely need to go through the codebase to understand its usage before changing it. This understanding effort could be drastically reduced if the variable name was clearer.

### Named conditions and magical numbers

Named conditions are helpful to set labels for complex conditions. Sometimes there are booleans that have more than 3 smaller conditions in themselves. In this case, it is good to name this big condition with a variable in order to bring more context to future readers.

```jsx
// BAD
if (
  user.isLogged() &&
  user.doesHavePrivileges() &&
  user.doesHaveEnoughBalance()
) {
  // ...
}

// GOOD
const isUserAllowedToWithdraw =
  user.isLogged() && user.doesHavePrivileges() && user.doesHaveEnoughBalance();

if (isUserAllowedToWithdraw) {
  // ...
}
```

The same happens with magical numbers. Magical numbers are numbers inside of conditions that lack context. Conditions accept any number of arithmetic comparisons and naming them will bring more context to the number itself, improving the code legibility. Example:

```jsx
// Bad
if (totalOfFailedRequests > 50) {
  notifyAdminsOfFailedRequests();
}

// Good
const FAILED_REQUESTS_NOTIFICATION_THRESHOLD = 50;

if (totalOfFailedRequests > FAILED_REQUESTS_NOTIFICATION_THRESHOLD) {
  notifyAdminsOfFailedRequests();
}
```

### Boolean suffixes

Another tip is to prefix named conditions. Following we have some suggestions:

- is

  - Example: `isUserAlreadyRegistered`

- are

  - Example: `areStatementsReady`

- does

  - Example: `doesUserExist`

- do

  - Example: `doUsersHavePrivileges`

- can

  - Example: `canUserAccessPage`

- has

  - Example: `hasUserReceivedNotification`

- have
  - Example: `haveUsersReceivedNotification`

### Methods and functions are specific, small, and concise

Methods and functions perform actions and using them more often is positive because they bring more verbs to the code since they perform actions. Methods make the code more humanized since now we have verbs (methods and functions) and nouns (variables and classes). However, it’s important to remember that methods and functions should:

- Do one simple thing, i.e. have just one responsibility
- Have a meaningful naming

By following the suggestions above, the code will have more methods. Since they have only one responsibility, they are easier to reuse, test, and understand. Otherwise, methods and functions with multiple responsibilities may not be easily reused.

A system with more methods and functions is more modulated. A system with simple methods and functions that have only one responsibility and have good names empowers Engineers to reuse these resources.

Let’s see this example:

```jsx
// BAD
function doesUserAndPasswordMatch(user, password) {
  const doesUserExist = Database.getUser(user, password);

  if (!doesUserExist) {
    return false;
  }

  notifyUserOfNewLogin(user);
  return true;
}

// GOOD
function doesUserAndPasswordMatch(username, password) {
  const doesUserExist = Database.getUser(user, password);

  if (!doesUserExist) {
    return false;
  }

  return true;
}

function Login() {
  if (doesUserAndPasswordMatch(username, password)) {
    notifyUserOfNewLogin();
    // code
  }
}
```

In the bad example above, the function `doesUserAndPasswordMatch` is doing more than one thing. It’s not possible to reuse it without notifying a user of a new login through `notifyUserOfNewLogin()`.

Now, let's assume we want to create a confirmation inside the system every time that the user does something critical, like a request for withdrawals. Inside the app, it will open a dialog requesting the user's password again. Can we reuse the `doesUserAndPasswordMatch` function? No, because it will notify the user, which is not the wanted behavior.

In the good example above, the function `doesUserAndPasswordMatch` has just one responsibility, which is matching username and password. Now we can reuse it without problems.

By following this tip we have these benefits:

- Small methods which are easy to maintain
- Improves code readability
- Easier to follow DRY

### **Only one level of indentation per item**

Keeping one level of indentation per item will improve the code readability and the separation of concerns. Every time that we have a second level of indentation, there is an opportunity to split this item. See the following examples to understand more.

Functions:

```jsx
// BAD
users.map((user) => {
  return {
    ...user,
    fullName: `${user.firstName} ${user.lastName}`,
  };
});

// GOOD
users.map(formatUser);

function formatUser(user) {
  return {
    ...user,
    fullName: `${user.firstName} ${user.lastName}`,
  };
}
```

Types:

```tsx
// BAD
type User {
	name: string;
	email: string;
  	address: {
		street: string;
		city: string;
		country: string;
		zipCode: string;
	}
}

// GOOD
type Address {
	street: string;
	city: string;
	country: string;
	zipCode: string;
}

type User {
	name: string;
	email: string;
	address: Address;
}
```

### Only necessary comments

The code should explain itself and that reduces the necessity of multiple comments. Although, comments are still useful for:

- Explain a decision
- Explain a known issue
- Any other context that the lines of code cannot explain by themselves

For example:

```jsx
// We have performed in that way because of the following issue
// https://github.com/1234/issue/4321

// CODE...
```

### Consistency throughout the codebase

The code should be consistent. The main goal is to have a codebase that seems to be maintained by a single person, even though there were several maintainers. Code Review is the right place to look for inconsistencies in the new code compared to the current one.

Consistency involves different layers of the code:

- Code Formatting/Styling
- Code Pattern
- Code Structure
- Architecture

### Conclusion

Code Legibility is a huge topic with many sub-topics. To learn more from them we strongly recommend reading [Lore Dev | Writing Code](https://lore.dev/development/writing-code) and [Willian Durand | Object Calisthenics](https://williamdurand.fr/2013/06/03/object-calisthenics/).

## Code Organization

The codebase should have an organized structure. A good structure is easy to follow, normally has tiny files, and separates concerns properly.

Organizing a codebase requires to group artifacts by domains, value, teams, features, and more. There are multiple approaches to organizing the codebase. As with almost everything in Software Engineering, the best approach depends on your project.

### Grouping by domain

The most common way to organize the codebase is by `domain`. For example, MVC and MVVM are architectures that group files by their domains. See this MVC example:

```
┣ 📂 tests
┣ 📂 models
┣ 📂 controllers
┣ 📂 views
┣ 📜 index.js
```

### Grouping by teams

In this way, artifacts are groupped by teams and their responsibilities. Very used for `monorepos`. For example:

```
┣ 📂 api
┣ 📂 ui
```

### Grouping by features

Grouping by feature makes easy to understand what the software does at a high level. For example:

```
┣ 📂 tests
┣ 📂 app
┃ ┗ 📂 blog
┃ ┗ 📂 feed
┃ ┗ 📂 comment
┃ ┗ 📂 admin
┣ 📜 .gitignore
┣ 📜 index.js
```

### Don't be clever, be simple

We strongly believe that simplicity is better than cleverness. It's possible to organize the codebase with clever names, which maybe makes sense for you, but will not make sense to other collaborators. Let's see this example:

```jsx
// BAD
┣ 📂 tests
┣ 📂 src
┃ ┗ 📂 atoms
┃ ┗ 📂 molecules
┃ ┗ 📂 organisms
┃ ┗ 📂 pages
```

This code organization promotes great modularity but it also provides more questions than answers. What is the difference between `atoms` and `molecules`? When should we add an `organism` over `molecule`? What is the difference between an `organism` and a `page`?

The goal is to bring simplicity and readability. Maybe we can keep the same modularity proposed before with better names like:

```jsx
// GOOD
┣ 📂 tests
┣ 📂 src
┃ ┗ 📂 simple-components
┃ ┗ 📂 components
┃ ┗ 📂 sections
┃ ┗ 📂 pages
```

This example has the same modularity as `Atomic Pattern`, but the names are easier to understand. Simple components will have `Buttons, Inputs, Labels`. Components will join simple components to achieve a goal like `NavigationBar, SearchInput, AppBar`. Sections will store a group of `components` like `HeaderSection, StatementsSection`. Pages will use different sections like `BlogPostPage, BlogFeedPage, AdminHomePage`.

### Conclusion

As we can see, there are multiple ways to organize the codebase. There is no right approach, it depends the project and the team. What works for project A, may not work for project B.

The main goal is to be simple and bring more value to code maintainers by making the project easier to read, understand, predict, and extend.

Finally, the defined organization should be kept by all engineers. New code should be consistent with the project organization.

## Third-party’s libraries

Normally projects rely on libraries and frameworks to build their foundation. We rarely start a project without using a framework. Thinking about Javascript, when we start a frontend project, some names come to our mind like React, Vue, and Angular. In the backend, Express, Fastify, and NestJS are known candidates too.

Code reviews should analyze how these frameworks and libraries are being used. It’s important to follow their best practices to achieve the best results in security, performance, and clean code.

When the codebase does not follow best practices from a particular framework, there is a high chance of compromising its performance and security, getting duplicated code, and wasting time on problems that have already been solved. Normally, frameworks and libraries had thought in many aspects to help engineers' lives and save them time.

By following the framework's best practices we can save development time, app performance, and app security. Any code that tries to solve a problem already solved by the framework should be rejected

## Style guide

The code style should be consistent throughout the codebase. The main benefit of keeping a consistent code style is the minimum effort that collaborators need to apply to read and understand the code.

For example, some people may like to use spaces over tabs, which produces different margins for blocks. Some collaborators also like to use double quotes for strings and others prefer single quotes instead. As we can see, these tiny differences may impact negatively the code's legibility.

It looks like a simple detail, but details matter. When there is a defined structure, our brains are prepared for it, our eyes will move across the code faster, we need to put less effort to decode different styles. With a standard, we can focus on what really matters instead of wasting brain energy on decoding different code appearances.

There are some tools that help to ensure the same style in the codebase like Linters, Prettier and more. Always ensure that the code that is being reviewed follows the same style guide.

## Design Principles

Code Reviewers ensure that Design Principles are followed.

### Separation of Concerns

The code has a good separation of concerns. There are well-defined layers throughout the codebase, separating scopes and responsibilities. Some layers to apply this principle:

- Classes
- Functions
- Data structures
- Folders
- Business rules (domains)

An app that contains a good separation of concerns will be easier to understand, follow, maintain, and extend. The app will be more consistent and organized, like a cleaned room. It’s easy to find your wallet when the room is cleaned and organized.

### YAGNI

"You aren't gonna need it" is a principle that says that an engineer should not add functionality until they are clear and necessary.

By following this principle we save time. When there is a real need, there are clear requirements. Otherwise, we may add unnecessary complexity that could make the codebase harder to maintain without any real benefit.

### KISS

“Keep It Simple Stupid” says that we should keep everything simple. Always go with the simplest option as the first call. Go with complex approaches only when trade-offs pay it off. KISS also stands for easier readability of code.

### DRY

“Don’t Repeat Yourself” speaks for itself, the code should not repeat itself. The code should be reused whenever possible.

> 💡 **Notes:** Keeping one responsibility for each method or component is really helpful to follow DRY. When the methods and components are clear and they do only one thing, it’s easier to reuse them without side-effects

### SOLID

SOLID is an acronym for 5 principles that makes the code easier to understand, maintain and be more flexible. Its principles are:

- **Single Responsibility Principle:** Each function should do only one thing. Each class should have only one responsibility/domain
- **Open Closed Principle:** The entity is open for extensions and closed for modifications
- **Liskov Substitute Principle:** It is possible to switch between subclasses without breaking the application
- **Interface Segregation Principle:** The system goes with contracts by using interfaces
- **Dependency Inversion Principle:** The system depends on abstractions (interfaces) upon implementations

Normally, more experienced engineers know how to apply these principles. Following them makes the codebase more uncoupled to particular technologies, frameworks, and implementations. For example, by following SOLID, it’s easy to switch from a Relational Database to a Non-Relational Database with little effort.

## Automated Tests

### No tests, no approval

Maybe, this is the simplest guideline from Code Reviews. If the PR does not have a good coverage of automated tests, the PR is not ready to be merged and to be deployed.

### Affirmative and simple assertions

Good PRs cover the business logic with affirmative and simple assertions like:

- `creates a new user`
- `deletes a user`
- `throws an error when user does not exist`

The code reviewer should be able to understand what the code is doing and how just by reading the automated tests and their sentences. If the automated tests don’t provide good documentation and guide for the reviewer and new engineers, definitely there is room for improvements.

### Descriptive inputs and outputs

The most basic workflow from computing is the IPO Model (Input, Process and Output). Applications always follow this model by Input, Process and Output. When we have descriptive inputs and outputs in automated tests, it’s easy to follow the usage of that method or component and what is its purpose (process).

A ready-to-go production code always provides descriptive inputs and outputs. For example:

```tsx
// Bad
it('lists users', () => {
	await createUser(user1);
	await createUser(user2);

	const users = await Users.getAll();

	expect(users[0].id).toBeDefined();
});

// Good
it('lists users', () => {
	await createUser(user1);
	await createUser(user2);

	const users = await Users.getAll();

	expect(users[0].id).toBeDefined();
	expect(users[0]).toMatchObject({
		name: "Kaleb Ironfield",
    	email: "kaleb@trio.dev",
		...
	});
});
```

Matching an object on some tests is a powerful tool to provide clearness of the output, especially for the most important fields. And this kind of assertion enables the extension of the `User` entity without breaking this test and we can reject timestamps fields like `createdAt` and `updatedAt`.

### AAA Pattern

Another great pattern to help with Test reading is the AAA Pattern. This pattern states that we should separate our tests into three different sections:

- **Arrange:** This section prepares all the data for the action
- **Act:** This section contains the action that should be tested
- **Assert:** This section wraps all assertion statements

So, now the tests should look like this:

```jsx
it('lists users', () => {
	// Arrange
	await createUser(user1);
	await createUser(user2);

	// Act
	const users = await Users.getAll();

	// Assert
	expect(users[0].id).toBeDefined();
	expect(users[0]).toMatchObject({
		name: "Kaleb Ironfield",
    email: "kaleb@trio.dev",
		...
	});
});
```

## Code Smells

We should review code looking for code smells to avoid future issues/consequences due to poor code merged without awareness. There are many code smells that we can produce, and to learn more about them, we suggest reading [Refactoring Guru | Code Smells](https://refactoring.guru/refactoring/smells). The most common are:

- Long methods
- Large classes
- Long parameter list
- Code repeating
- Unnecessary inheritance
- Complex switch statements
- Strong dependency between items (by not following OCP)
- Lazy classes

## Technical Debts

In Code Reviews, we may face Technical Debt. Technical Debt is something that you can improve, but you are not able to apply it at this moment because of many reasons like delayed deadlines, conflict with priorities, and more.

The best recommendation is to not collect Technical Debts and solve them at the same moment they are created. Although life is chaotic, the code is not 100% perfect, and Technical Debts are inevitable.

In this case, be aware of all Technical Debts that this code has and follow up with their solution. Technical Debits could be unmerciful and charge a lot of fees with time as a Financial debt, for example. With time, they could become harder to solve!

## Security

Security is an important dimension to check constantly. The Code Reviewer should be aware of the most common attacks and how to protect the code against those security issues. We highly suggest reading [OWASP Top Ten Attacks for Web Applications](https://owasp.org/www-project-top-ten/).

The most common attacks for web development are:

- [SQL Injection](https://owasp.org/www-community/attacks/SQL_Injection)
- [Web Parameter Tampering](https://owasp.org/www-community/attacks/Web_Parameter_Tampering)
- [HTTP Parameter Pollution](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/04-Testing_for_HTTP_Parameter_Pollution)
- [XSS](https://owasp.org/www-community/attacks/xss/)
- [Improper Error Handling](https://owasp.org/www-community/Improper_Error_Handling)
- [Cross Site Request Forgery](https://owasp.org/www-community/attacks/csrf)

# Tips to make you a better Code Reviewer

## No rush

When you need to review code, take a deep breath and be ready to spend a good amount of time on it. Disable your notifications, get a glass of water or coffee and enjoy the view! Treating a Code Review with this importance will bring better results for you as a Code Reviewer. Consequently, your good Code Review will bring a positive impact on the PR owner and finally to the client and company.

No rush! Go deeper into details and help your teammates by catching problems that the team may missed.

## Quality first, always!

Always keep the quality as the first and most important value in the codebase. Going well is going faster! A good line of code pushes Engineers to keep writing more good lines of code.

## Track your Technical Debts

Technical Debts are problematic! They will charge you someday and it could be a big undesired surprise. Always prefer going with extreme quality first and paying all these debts at the same moment they are created.

However, if for some reason the project should go forward compromising the quality, track all the Technical Debts. It’s important to refactor them as soon as possible. Remember that Financial debts have extra fees over time. It works exactly like that on Technical Debts either.

## Clear communication

Do not give room for misunderstandings in your comments. The communication should be simple, objective, and easy to follow. With that, the PR owner will be able to learn from you and apply the requested changes without many interactions.

## Review your own PR before asking for reviews

Another good practice is to review your PR before asking for reviews. Some benefits by doing this are:

- Your PR will improve. Your code will be more ready to be deployed than before
- You will save time from your team members since your PR looks better
- With time, you will be more aware of the most common errors from Engineers because you learned from your own mistakes. In other words, reviewing your own PRs will make you a better Code Reviewer with time

## Judge your comments

Code reviewers should always use good judgment before submitting a review comment. Bad comments can lead to multiple unnecessary rounds of reviews that could drain the time development of the entire team. Good comments will deal the team achieve the goal which is to merge the PR and deliver value to the final client.

Judge your comments before submitting them. Ensure that your comments are good enough to be submitted. Sometimes, the best comment is the comment that we don’t make. There are some moments when pair programming will be more valuable than a comment.

## Code Review culture

Emphasize the Code Review culture within your engineering team. Everyone should be able to review each other's code. Getting multiple reviews before deploying a PR can be really valuable.

## Revewing own Pull Requests before asking for reviews

Often Software Engineers ask for reviews on Pull Requests that are not completely ready. They have typos, failing automated tests, pushed unnecessary files, etc.

We encourage the Pull Request owners to create the habit to review their own Pull Requests before asking for reviews.

## Don't take comments and suggestions personally

When your Pull Requests are being reviewed, don't take comments to the personal side. It's not about you! The team is working to provide the best to the company, the client, and to the software itself. Take it as an opportunity to grow.

When you are reviewing a Pull Request, always add the rationale of a feedback comment. Give enough context and reasons for your suggestions.

# Conclusion

Code Reviewers should pay attention to every detail from every code line. It’s not a simple task, it demands knowledge, patience, and attention.

The code reviewer is someone that truly cares about the code and its quality but also knows how to deal with people with empathy, respect, clarity, and objectiveness.

In the end, reviewing code is a skill that you improve with practice. Do not give up and keep improving!

# Resources

This is a list of resources that you can consume to go deeper and improve as a Code Reviewer.

- [Lore Dev | Writing Code](https://lore.dev/development/writing-code)
- [Lore Dev | Refactoring](https://lore.dev/development/refactoring)
- [Refactoring Guru | Code Smells](https://refactoring.guru/refactoring/smells)
- [Willian Durand | Object Calisthenics](https://williamdurand.fr/2013/06/03/object-calisthenics/)
