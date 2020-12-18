---
id: writing-code
title: Writing Code
sidebar_label: Writing Code
---

> “Code is bad. It rots. It requires periodic maintenance. It has bugs that need to be found. New features mean old code has to be adapted.
>
> The more code you have, the more places there are for bugs to hide. The longer checkouts or compiles take. The longer it takes a new employee to make sense of your system. If you have to refactor there's more stuff to move around.” - Rich Skrenta, Author of Code is our enemy

We should always strive to write the best code possible, which often means writing as few lines of code as possible, in the simplest possible way, to solve a specific problem. This topic is meant to help you figure out how to achieve that.

## Define and Keep a Consistent Style Guide

Have you ever joined a project where sometimes the *code_was_written_like_this* and *Sometimes-Like-This*? I know you have. We all have. Simple inconsistencies in code can result in difficulty maintaining codebases.

Development is much better when you can easily find a function or file, or when you can quickly read through and understand what the code does. That is what I call readability. One step to achieve this is by defining and enforcing a consistent style guide. A style guide must be understood and followed by everyone who touches any of the source code in a project. 

It's unlikely that you will define all possible rules at once, so your style guide is something that keeps growing, transforming, and adapting over time as the project needs change. The style guide MUST be consistent, and, the team must understand and follow any new rules as they are defined. If this requires the team to [meet together](https://forum.wordreference.com/threads/meet-together.1006928/) to discuss a new rule, then, so be it! The consistency will improve the team’s overall productivity over time. 

When writing a new style guide, a good way to start is to read through the previous code you and your teammates have written in the past, so you can see the good subjects to be agreed on with your team. It is good to notice this process is something that you will keep repeating whenever you find any sort of inconsistency.

Let's list a few topics that you might want to use when creating your own style guide. These topics can vary depending on the language or project needs, but the important thing here is to list some samples and to understand that they must be explicitly defined:

- Case styling for folder, files, classes, functions, variables, constants, etc.
- PascalCase
- camelCase
- lazycase
- snake_case / underscore_case
- kebab-case / dash-case
- Block indentations
- Line length
- Ordering of method and function definitions
- Grouping with parentheses
- Comments
- Naming
- Folder and file organization
- Proximity
- Nested statements
- … and more

You will know that you've achieved code consistency when someone else performs a code review on something you wrote and notices where you broke the project's rules. Consistency is the key to achieve maintainability in the long term.

## Clean Code

> "Any fool can write code that a computer can understand. Good programmers write code that humans can understand." - Martin Fowler

> "Master programmers think of systems as stories to be told rather than programs to be written" - Robert C. Martin

Clean code is not just a simple rule but a development philosophy whose main goal is to follow techniques to make your code easily readable and understandable.

The productivity of a developer is directly related to the quality of the code they are working with. Refactoring a piece of code that has been poorly written can often take significantly longer than a similar piece of clean, clear, and concise code. 

Most developers spend more time reading and understanding code than actually writing it. Robert C. Martin already said: “Indeed, the ratio of time spent reading versus writing is well over 10 to 1. We are constantly reading old code as part of the effort to write new code. ...[Therefore,] making it easy to read makes it easier to write.”. So if you really want to be a better developer, there's no other way but to write cleaner code.

> "Most managers want the truth, even when they don’t act like it. Most managers want good code, even when they are obsessing about the schedule. They may defend the schedule and requirements with passion; but that’s their job. It’s your job to defend the code with equal passion." - Robert C. Martin

### Meaningful Naming

You probably have come across poor variable naming that cost you valuable time to figure out its meaning. This is probably not how you should spend your time.

#### Use intention-revealing names

A good variable naming can tell exactly what is going on without even needing to read the rest of the implementation.

```es6
// Bad
const user1 = new User();
const user2 = new User({ admin: true });

// Good
const regularUser = new User();
const adminUser = new User({ admin: true });
```

```es6
// Bad
const users2 = users.filter(user => user.role === 'admin');
return users2[0];

// Good
const adminUsers = users.filter(user => user.role === 'admin');
return adminUsers[0];

// Better
const [firstAdminUser] = users.filter(user => user.role === 'admin');
return firstAdminUser;
```

#### Use pronounceable names

Humans are good at words and words are, by definition, pronounceable. If you can't pronounce it, you can't discuss it without sounding weird. Remember that code must be executed by computers but read by humans.

```es6
// Bad
const ymdDate = new Date('Y-m-d');

// Good
const formattedDate = new Date('Y-m-d');
```

#### Never use numbers to name

Appending a digit to a variable, function, or class name can greatly decrease code readability. Usually, the numbers end up being meaningless and hide the real purpose of the name. What does the variable `user1` actually mean? Is it the first user of the application? Is it the user ranked in the first place? Or could it just be a meaningless name that should be refactored to be something else? In the rare instance where you need a number in a name, it is recommended that you write out the actual word, or use a synonym. For example:

```es6
// Bad
const user1 = new User();
const user2 = new User({ admin: true });

// Good
const regularUser = new User();
const adminUser = new User({ admin: true });
```

```es6
// Bad
const auth2NetApi = new Auth();

// Good
const authToNetApi = new Auth();
```

```es6
// Bad
users.filter((user1, user2) => {
  return user1.id - user2.id;
});

// Good
users.filter(function filterUserByIdAsc(firstUser, secondUser) {
  return firstUser.id - secondUser.id;
});
```

#### Avoid abbreviations as much as possible

Coding itself is already hard to do as clearly as possible. So, anything that makes it harder to understand or anything that leads to subjectivity might be not good.

We as developers are always trying to make things shorter, easier. But when it comes to short variable names for example, it may backfire. It's always better to make things very explicit instead. [The obvious must be said](https://www.lesswrong.com/posts/6phFYpNQH9SmWL9Jt/on-saying-the-obvious): if you try to descript the whole context of a variable, the name might be too long, but it still is preferable to have an understandable name than a name that I have to read a legend or a dictionary somewhere else in order to understand it. Full names may avoid ambiguity.

Abbreviations even when they’re [well-known](https://github.com/kisvegabor/abbreviations-in-code), still have a chance that someone else doesn’t know that. For example, you probably have seen some code naming as *i18n*, and I'm pretty sure that you did not instantly understand the meaning of it for the first time. You probably had to search and find out that it means i**nternationalizatio**n. So, even the most known abbreviations sometimes can not be easily understood. Of course, it's up to you to decide whether to use abbreviations or not because every rule has its own exception. So carefully decide the abbreviations that you would use. Here a few examples:

```es6
// Bad
user.setRole('mng');

// Good
user.setRole('manager');
```

```es6
// Bad
function getWin() {}

// Good
function getWindow() {}
```

### Consistent Naming

Before even talking about naming, you should care about defining the Natural Language that will be used throughout the entire codebase. Many projects use English for that because it reaches a good part of the developers' understanding. Feel free to choose your own Natural Language, but make sure to be consistent about it.

Naturally naming is a hard thing to do but there are benefits of doing it consistently, such as better understanding of the concepts of your application. Otherwise, it might cause misunderstanding and make you spend more time to figure out why names are different to represent the same thing.

Sometimes there are many different names to represent the very same concept. So, make sure to choose the name that better fits your application needs and keep it consistent. You could take even more advantage when using consistent naming across different applications in your project or company.

A good sample is when you use the word `Error` and in another file you use `Exception`. What is the difference between both? If there is no difference, it sounds like you should choose only one of them and keep it consistent.

### Clearer statements and flow controls

Statements and flow controls are already complex by nature. It’s our responsibility to make them as easy as possible to read and understand. Remember that code is meant to be executed by a machine but read by humans.

In order to fresh our minds, a statement is a syntactic unit that expresses an action (e.g. such as `for`, `while`, `do while`) and flow controls order instructions or function calls that are executed or evaluated.

#### Use curly braces {} whenever is possible

Many programming languages support writing statements and flow controls without using curly braces. Some languages do not even support curly braces, but those that support them can be leveraged to help make boundaries clearer. Since we should always stick to the principle of making code easy to understand, you should use curly braces whenever you can instead of not using them.

```es6
// Bad
if (authenticatedUser.role !== 'admin')
  forbid();
return allow();

// Good
if (authenticatedUser.role !== 'admin') {
  forbid();
}

return allow();
```

Here’s another sample:

```es6
// Bad
if (!isAuthenticated) throw new NotAuthenticatedError();

// Bad
const authenticate = ({ username, password }) => findUserByUsername(username).then(buildUserPasswordMatcher(password));
```

The above code can make the boundaries of the statement difficult to understand. Always try to make the boundaries clear and very explicit:

```es6
// Good
if (!isAuthenticated) {
  throw new NotAuthenticatedError();
}

// Good
const authenticate = ({ username, password }) => {
  return findUserByUsername(username)
    .then(buildUserPasswordMatcher(password);
}
```

#### Returning implicit booleans

An implicit return boolean is when you add unnecessary flow control just to return a boolean. It should be avoided in order to make the code more clear and concise.

```es6
// Bad
function isAuthorized() {
  if (authenticatedUser.role === 'admin') {
    return true;
  }

  return false;
}

// Good
function isAuthorized() {
  return authenticatedUser.role === 'admin';
}
```

#### Named booleans

Have you already seen those `if` statements with a lot of `OR/AND` operators really hard to understand? What if we could make that easier to understand? Let’s split and name the boolean statements in order to achieve that:

```es6
// Bad
if (authenticatedUser && authenticatedUser.role === 'admin' && authenticatedUser.isActive && ((authenticatedUser.plan.isTrial && authenticatedUser.plan.trialExpireAt < Date.now()) || !authenticatedUser.plan.isTrial)) {
  return allow();
}

forbid();

// Good
const isNotAuthenticated = authenticatedUser === null;

if (isNotAuthenticated) {
  forbid();
}

const isUserAdmin = authenticatedUser.role === 'admin';
const isUserActive = authenticatedUser.isActive;
const isTrialPlan = authenticatedUser.plan.isTrial;
const isTrialPlanActive = isTrialPlan && authenticatedUser.plan.trialExpireAt < Date.now();
const isNotTrialPlan = !isTrialPlan;
const isPlanActive = isNotTrialPlan || isTrialPlanActive;

if (isUserAdmin && isUserActive && isPlanActive) {
  return allow();
}

forbid();
```

Even though the code is longer, it is much more expressive and easier to read.

### Comments

You probably have already heard that comments are a good way to tell others how a piece of code is supposed to work, right? What if I tell you that you’re probably doing it in the wrong way? What if there are more effective approaches to do it so? This topic will make you at least think about what you know about comments.

Code must be self documenting. Comments and documentations enhance the code and standardize procedures.

Comments are not a rule to be followed without thinking about them. Comments are not supposed to describe what the algorithm is doing, that’s the responsibility of the code itself. Let’s learn how to use it wisely.

> "Don’t comment bad code — rewrite it." - Brian W. Kernighan

#### Don't comment bad code, rewrite it

People usually misunderstand the real purpose of comments. So if you have a comment to explain the intent of a piece of code, you apparently also misunderstood it. Comments don’t make up for bad code.

Languages are expressive enough nowadays and we have the talent to clearly express ourselves through code. We may not need comments. The older the comment is, the farther it is from the code it describes.

Is it time to write comments or to refactor the code? Keep reading, and let’s see a few samples about good and bad comments.

#### Good comments

Every rule has its exception, so comments aren’t different. Let’s see a few samples where comments can fit rightly.

##### Legal comments

Copyright and authorship statements of the project or even of each file.

##### Explanation of intent

Sometimes a comment goes beyond just useful information about the implementation and provides the intent behind a decision. Related material and further thoughts about it should be attached as well.

##### Amplification

A comment may be used to amplify the importance of some decision made, that otherwise may raise side-effects and consequences.

#### Bad Comments

You should use comments wisely. They can lead up to misconfusion.

##### Obvious comments

You should not spend time commenting on every variable or function like if it was a rule. Comments like those just clutter up the code and lend to disorganization. Naming functions and variables often are the best way to avoid that kind of comments. Use comments to express more than just what could be understood by reading a variable or a function name.

##### Versioning code

Do not comment on a piece of code thinking about using it later nor comment the history of it, like what happened through time. That’s the role of a version control system like Git. It just makes the code look like piled up garbage.

##### Closing brace comments

Take a step back and think about closing brace comments like a code smell. You should not create comments like these. Although it might make sense because your code is too deeply nested, it sounds like the perfect time to break down your code into smaller functions and refactor it.

##### Misleading comments

Even with the best intentions, you have to make sure to write a clear statement in your comments where anyone can read and fully understand about its intentions and purpose. Write comments accurately and precisely. Don’t use external references that aren’t accessible to who is reading or that just makes things harder to understand.

### Simplicity Over Cleverness

It's always frustrating when you start reading a file and it takes more effort than it should, and your brain comes to a screeching halt. You're forced to stop and interpret an overly complex handful of lines.

You should not be worried about writing clever lines of code. That may backfire and goes against simplicity and readability. Remember the easier you read the code, the simpler it is. Clearness is better than cleverness.

> "Fools ignore complexity. Pragmatists suffer it. Some can avoid it. Geniuses remove it." - Alan Perlis

Have you ever heard about the [KISS principle](https://en.wikipedia.org/wiki/KISS_principle)? I know it can sound rude but that's about being so easy that anyone can understand and it becomes stupid *(i.e. [lacking intelligence](https://dictionary.cambridge.org/us/dictionary/english/stupid))*. You should use your cleverness to keep the algorithm as simple as possible. Sometimes, it's really tempting to write less code, but are these spared lines adding more complexity than saving time to read?

#### Brevity

It’s a falsehood if you think that you’re saving time to write shorter sentences and shorter lines of code. Saving time, but saving time for who? Think always about how easy it is to someone else to read and understand the code that you’re writing. You should save some time for them.

```es6
// Bad
function getNextSize(i) {
  // multiply it by four and make sure it is positive
  return i > 0 ? i << 2 : ~(i << 2) + 1;
}

// Good
function getNextSize(currentSize) {
  const nextSize = currentSize * 4;
  const isNextSizePositive = nextSize > 0;

  if (isNextSizePositive) {
    return nextSize;
  }

  const positiveNextSize = nextSize * -1;
  return positiveNextSize;
}
```

#### Early optimizations

You can not simply start coding without thinking a little bit about efficiency. Being able to efficiently optimize is only possible if you already have had experience coding something similar before, so some standard optimizations are clear and natural to you.

You should not invest too much time optimizing everything if you don't even know the benefits or the impacts of those optimizations in your application. An algorithm to consider is: *the invested time * the benefit * the complexity*. 

Whenever you start writing code from scratch, do not spend too much time thinking about efficiency and optimizations. Doing so will often lead you to add useless complexities that were not properly measured or evaluated and may not even be needed.

A better strategy is to invest time implementing and configuring tools to measure and monitor your application. These can help you figure out the parts of your application that can benefit from optimization.

Only start optimizing when you clearly understand the performance issues that you're facing and you have the best possible solution to solve them.

#### Early abstractions

Just like [early optimizations](#early-optimizations) can be dangerous to your code, early abstractions can create needless complexities as well. Abstractions are meant to avoid duplicated lines of code, but you have to make sure to need it because they usually turn your simple code into inheritances or compositions that might make it harder for other developers to read and fully understand how they work. Abstractions have their cost to be created and, if wrongly done, they may require some cognitive overhead.

Be sure to firstly face the problem of duplicated algorithms and to have abstractions as an option to solve it. And if you decide to go for it, be also sure to well design it before writing it. If you can’t go through all that effort, it might be better to not use abstractions at all.

#### Avoid overwhelming your project

It’s pretty common to find a lot of tutorials teaching how to build your web application using Ruby on Rails and React, or even Phoenix and Vue. Have you already stopped to think if these stack technologies are really needed or are they just overwhelming your project and adding unnecessary complexity to it?

We have to evaluate if the framework that we chose is really a wise choice made. For example, if you want to write a web API using [Ruby on Rails](https://rubyonrails.org/), you will likely want [to disable unnecessary dependencies](https://guides.rubyonrails.org/api_app.html) like the library that compiles CSS and JavaScript. Or depending on your needs you could use something even simpler like [Sinatra](http://sinatrarb.com/).

Don’t follow a tutorial blindly, make your choices wisely. Always prefer the simplest way, where your choice will still fit the needs but adding as less complexity as possible. It makes the project easier to maintain.

### Easy Application Programming Interface to Work With

Beyond making the implementation of our functions easy to understand, it’s also important to make them easy to use.

#### Unnamed vs. Named parameters

You probably have already seen some function calls passing many parameters that are just hard to understand, right? Some programming languages like PHP, JavaScript, Ruby and others support a way to name the parameters. An additional benefit is that the order of the parameters no longer matters as you are defining the variable they map to in the call.

It’s important to understand the problem faced and the used concept to solve it. Don’t worry about the language syntax itself. Let’s see a few samples:

```es6
// Bad
requestFriendship(requesterUser, requestedUser, true, false, true);

// Good
requestFriendship({
  requestedUser: requestedUser,
  watchUpdates: true,
  requesterUser: requesterUser,
  markAsFavorite: false,
  sendNotification: true
});
```

Much better, right? You easily find out exactly what the parameter names are.

#### Facade pattern

Sometimes, interfaces can be complex to use or just too verbose because you have to build the same objects over and over. That’s exactly when it might be a good idea to think about refactoring the API, or to implement the Facade pattern where you will be able to reduce the lines of the structural code. Let’s see a few samples:

```es6
// Bad
const friendshipRequest = new FriendshipRequest({
  requesterUser: requesterUser,
  requestedUser: requestedUser
});

friendshipRequest.setIsFavorite(true);
friendshipRequest.setWatchUpdates(true);

const requestNotification = new FriendshipRequestNotification({
  friendshipRequest: friendshipRequest
});

const requestedUserDevice = new UserDevice({ user: requestedUser });
requestNotification.sendTo(requestedUserDevice);

// Good
function requestFriendship({
  requesterUser,
  requestedUser,
  watchUpdates,
  markAsFavorite,
  sendNotification
}) {
  const friendshipRequest = new FriendshipRequest({
    requesterUser: requesterUser,
    requestedUser: requestedUser
  });

  friendshipRequest.setIsFavorite(markAsFavorite);
  friendshipRequest.setWatchUpdates(watchUpdates);

  const requestNotification = new FriendshipRequestNotification({
    friendshipRequest: friendshipRequest
  });

  if (sendNotification) {
    const requestedUserDevice = new UserDevice({ user: requestedUser });
    requestNotification.sendTo(requestedUserDevice);
  }

  return friendshipRequest;
}

requestFriendship({
  requestedUser: requestedUser,
  watchUpdates: true,
  requesterUser: requesterUser,
  markAsFavorite: false,
  sendNotification: true
});
```

A few lines  of structural code were abstracted to a function, and now the usage of `requestFriendship` is much cleaner and easier to read.

This structural pattern is known as [Facade pattern](https://en.wikipedia.org/wiki/Facade_pattern), but you get to know others [structural patterns](https://en.wikipedia.org/wiki/Software_design_pattern#Structural_patterns).

### Proximity

Whenever you are writing classes or functions, it’s important to keep related variables close to each other. Otherwise, it can become more difficult to follow their usage through the code flow. The proximity between used functions and variables matters.

#### Variables

Variables should be written as late as possible in order to avoid server resources consumption but always as close as possible to their usage. It might be not true when you must declare in advance the variable in certain scenarios such as in getters and setters of Java classes.

Whenever possible, the proximity of variables to their usage make the code easier to understand.

```es6
// Bad
function reportTotalPaidAmountOfOrdersByUser(user) {
  const reporter = buildReporter();
  reporter.to(getAdministrators());

  const userOrders = getOrdersByUser(user);

  if (!user.isActive) {
    return false;
  }

  // Many lines of code omitted...

  reporter.report(totalPaidAmountOfOrders);
}

// Good
function reportTotalPaidAmountOfOrdersByUser(user) {
  if (!user.isActive) {
    return false;
  }

  const userOrders = getOrdersByUser(user);

  // Many lines of code omitted...

  const reporter = buildReporter();
  reporter.to(getAdministrators());
  reporter.report(totalPaidAmountOfOrders);
}
```

#### Functions

It's awful when you have to excessively keep scrolling a file and read a lot of lines in order to find the implementation of an used function. You should keep functions sorted by the way they are called.

```es6
// Bad
function getAdministrators() {
  // ...
}

function buildReporter() {
  // ...
}

function getOrdersByUser() {
  // ...
}

function reportTotalPaidAmountOfOrdersByUser(user) {
  if (!user.isActive) {
    return false;
  }

  const userOrders = getOrdersByUser(user);

  // ...

  const reporter = buildReporter();
  reporter.to(getAdministrators());
  reporter.report(totalPaidAmountOfOrders);
}

// Good
function reportTotalPaidAmountOfOrdersByUser(user) {
  if (!user.isActive) {
    return false;
  }

  const userOrders = getOrdersByUser(user);

  // ...

  const reporter = buildReporter();
  reporter.to(getAdministrators());
  reporter.report(totalPaidAmountOfOrders);
}

function getOrdersByUser() {
  // ...
}

function buildReporter() {
  // ...
}

function getAdministrators() {
  // ...
}
```

### Deep nesting is a bad idea

Deep nesting is when you write code with multiple levels of indentation. It often means a [code smell](https://en.wikipedia.org/wiki/Code_smell). Deep nesting makes your code harder to read and to understand the context:

```es6
// Bad
if (authenticatedUser) {
  if (authenticatedUser.role === 'admin') {
    if (authenticatedUser.isActive) {
      if (authenticatedUser.plan.isTrial) {
        if (authenticatedUser.plan.trialExpireAt < Date.now()) {
          return allow();
        }
      }
    }
  }
}
```

The solution is really specific for each scenario. In this case, the problem is the [deeply nested flow statements](#deeply-nested-flow-statements).

#### Deeply nested flow statements

It occurs usually when you write complex branching statements where flow actions can be triggered in many places.

```es6
// Bad
if (authenticatedUser) {
  if (authenticatedUser.role === 'admin') {
    if (authenticatedUser.isActive) {
      if (authenticatedUser.plan.isTrial) {
        if (authenticatedUser.plan.trialExpireAt < Date.now()) {
          return allow();
        } else {
          return forbid();
        }
      } else if (authenticatedUser.plan.isPaid()) {
        return allow();
      } else {
        return forbid();
      }
    } else {
      return forbid();
    }
  } else {
    return forbid();
  }
} else {
  log('The user is not authenticated.');
  return forbid();
}
```

Check it out how would be a refactoring of that:

```es6
// Good
if (!authenticatedUser) {
  log('The user is not authenticated.');
  return forbid();
}

const isAdminAndActive = authenticatedUser.role === 'admin' &&
  authenticatedUser.isActive;

if (!isAdminAndActive) {
  return forbid();
}

const isTrialPlanValid = authenticatedUser.plan.isTrial &&
  authenticatedUser.plan.trialExpireAt < Date.now();

const isPlanValid = isTrialPlanValid ||
  authenticatedUser.plan.isPaid();

if (!isPlanValid) {
  return forbid();
}

return allow();
```

##### Early `return`

You do not need to necessarily use `else` statements to return. You should weigh and figure out what is the longest branch: is it the `if` block or is it the `else` block?

```es6
// Bad
if (authenticatedUser) {
  // Here is a really long block...
} else {
  return forbid();
}

// Good
if (!authenticatedUser) {
  return forbid();
}

// Here is a really long block...
```

##### Merge test clauses

```es6
// Bad
if (authenticatedUser) {
  if (authenticatedUser.role === 'admin') {
    if (authenticatedUser.isActive) {
      return allow();
    }
  }
}

// Good
if (authenticatedUser && authenticatedUser.role === 'admin' && authenticatedUser.isActive) {
  return allow();
}
```

There is even a better way, where you can [name boolean variables](#named-booleans).

```es6
// Better
const isAuthenticatedAdminAndActive = authenticatedUser &&
  authenticatedUser.role === 'admin' &&
  authenticatedUser.isActive;

if (isAuthenticatedAdminAndActive) {
  return allow();
}
```

##### Avoid using `else`

It’s often used along with earlier returns and it can drastically reduce the complexity and levels of indentation.

```es6
// Bad
if (authenticatedUser) {
  return allow();
} else {
  return forbid();
}

// Good
if (authenticatedUser) {
  return allow();
}

return forbid();
```

#### Nested loops

Almost all languages support some sort of loop control to iterate over multidimensional data and when loops are nested to each other, it can be messy. Nested loops can be replaced by flatter structures.

```es6
// Bad
function hasUserEverLikedAnyPremiumPost(user) {
  for (var x = 0; x < posts.length; x++) {
    if (posts[x].isPremium) {
      for (var y = 0; y < posts[y].likes.length; y++) {
        if (posts[x].likes[y].userId === user.id) {
          return true;
        }
      }
    }
  }
}
```

The sample above contains three nested loops to iterate all authors, and then all of each author’s posts, and finally it iterates each posts’ like to check whether the user has ever reacted with like or not. There are trivial points in that algorithm that should be reviewed like hard readability due to multiple indentation levels and poor naming of variables.

##### Early `return`

You can use early returns to avoid levels of indentation. e.g.

```es6
// Good
function hasUserEverLikedAnyPremiumPost(user) {
  for (var x = 0; x < posts.length; x++) {
    if (!posts[x].isPremium) {
      break;
    }

    for (var y = 0; y < posts[y].likes.length; y++) {
      if (posts[x].likes[y].userId === user.id) {
        return true;
      }
    }
  }
}
```

##### Imperative vs. declarative interfaces

Nowadays language syntaxes are plenty powerful to make the code more readable than it was in the past. One of these powers is the ability to use declarative interfaces over imperative interfaces. It makes the code closer to our natural language. e.g.

```es6
// Good
function hasUserEverLikedAnyPremiumPost(user) {
  return posts.filter(maybePremiumPost => maybePremiumPost.isPremium)
    .reduce((flattenListOfLikes, listOfPostLikes) => {
      return flattenListOfLikes.concat(listOfPostLikes);
    }, [])
    .some(maybeUserLike => maybeUserLike.userId === user.id);
}
```

### Deleting Unnecessary Code

It might be considered less painful to add and write new features instead of refactoring existing code because when refactoring, you tend to read more lines of code. In both cases, developers rarely have the culture of finding and removing unnecessary code from the application.

Unnecessary code means lines that can be avoided, omitted or just written simpler in order to keep the codebase away from obsolescence.

Removing unnecessary code is not something usual because of many reasons, and one of them is because it might be scary to remove lines that you are not so sure about their usage. It just does not feel safe.


What could give you safety for removing unnecessary code or even just refactoring to make the code simpler? A good coverage of automated tests makes any development process safer and easier because almost any line of code wrongly changed or moved will result in tests failing.

But why should unnecessary code really be removed? Unnecessary code must be found and removed, otherwise leaving it might be an obstacle to other developers to understand. It leads to more complexity and confusion when reading the codebase.

When removing unnecessary code becomes a natural process of development in your application, it makes you try harder to maintain the codebase as clean as possible. It usually means that less legacy code will exist and other developers can feel safer because there are more parts of the application that are being regularly touched.

> Deleting dead code is not a technical problem; it is a problem of mindset and culture. - Kevlin Henney

## Separation of Concerns

You probably have already seen some huge files containing thousands of lines of code, that is basically, the entire application. It probably happened because the project architecture was poorly designed and the boundaries between various parts of the application do not exist.

You can think of the concept of Separation of Concerns as having well-defined design boundaries for your application. When there are well-separated layers, upgrades are easier, there is more code reusability, and greater independent development. These boundaries can be made of modules or layers.

A module is a Unit of Composition. When you speak of modules, you are usually referring to individual building blocks that connect with other building blocks. A module performs a single, elementary function, which is not useful by itself. A module can be developed independently and you can treat it as a black box without having to know how it works. In other words, a module can expose a public interface where other modules can consume and vice-versa but still hides private implementation. It is easier to develop a small module rather than refactoring the entire complex system.

On the other hand, a layer can be thought of as an abstraction of services that work on a similar conceptual level. For example, if your web app needs to communicate with the server using TCP, you will probably end up using HTTP, which operates as a communication layer.

Communication with HTTP is made up of a request made by your app and a response back made by the server. There are several rules and subprotocols that HTTP follows but the reason you use it is so that you can connect and talk to the server. You could replace it for another communication layer, such as WebSockets, and it could still fit the requirements when communicating to the server.

### Some Examples of Separations

#### Layers

One design principle says that applications should be separated into three primary layers:

- Presentation OR View Layer
- Business Logic OR Data Layer
- Data Access OR Persistence Layer

So for example, if you always keep the presentation separated from the business layer, it becomes easy to develop or even swap out one without affecting the other. Separate does not only mean in different namespaces or folders or files, it also means that the code base from both layers should be decoupled, well-separated and still able to connect them through function calls.

For example, keeping the Presentation Layer separated from the Business Layer, development is often cleaner, and the underlying technologies used within those layers can even be swapped out without other parts of the application being impacted. This is more than having different namespaces, folders, and files.

It also means that the layers within the code base should be decoupled. In this example, the Business Layer is where any business rules are computed, while the Presentation Layer performs the task of making the output from the Business Layer look nice and handling user input. 

##### Presentation / Interface Layer

It is totally responsible for making the application available to the user. It interprets and reacts to the user's actions by calling the other layers. It works like a translator of data and business rules to an interface by a process called rendering. This is the only layer users are able to see and directly interact with.

##### Business Logic / Data Layer

This layer can be considered the most important one of your application. It knows all models and their relationships and also enforces business rules that must be strictly followed. It is also responsible for processing and mutating the model records of your Persistence Layer. It directly interacts with the Persistence Layer and is usually consumed by the Presentation Layer.

##### Data Access / Persistence Layer

As its own name implies, this layer persists records to a data store, such as a database. It is often used with some **O**bject **R**elational **M**apper (ORM) framework that makes it easier for records to become data model objects. It is important to note this layer should not contain business logic rules, but instead provide an interface so the Business Logic Layer can access persisted data.

### Reading Code of Masters

As with everything in life when you want to succeed, you should learn from those who have already made it through that path. It means you will get more and more used to good code as much as you live and breath that.

There is no other way, you need to find out what good code is in its many shapes and concepts so you can understand why and how it works in order to write your own good code and even to form your own opinion about it.

You probably have used some good open source frameworks, libraries, and even some applications providing the public code base in site repositories, such as GitHub or GitLab. You should always keep yourself curious about how that functionality works and take a look at the source code of it. After a while, you will probably get so used to this habit and may eventually contribute to the projects, but that's another thread you will read in this document.