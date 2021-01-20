---
id: error-handling
title: Error Handling
sidebar_label: Error Handling
---

Before talking about handling errors, you have to identify exactly what part of the Separation of Concerns you are writing and not merely spreading `try` and `catch` statements across the codebase. In reality, it might mean not to use `try` and `catch` statements at all.

Having too many `catch` statements in your application probably means a code smells and can be improved. It can be even worse when you have `catch` statements that do not do anything meaning your application might be failing silently. For example:

```es6
function buildDatabaseConnection() {
try {
	return DatabaseBuilder.build();
} catch (error) {}
}

function getAllUsers() {
	try {
		const database = buildDatabaseConnection();
		...
	} catch (error) {}
}
```

Have you seen the sample above in your application? There are two places where errors are caught, and both of them fail silently.  
 
Errors exist for one reason: you should know when they break your application, to fix them, so they do not happen again.  

You will only want to catch an error when you want to retry the failed statement or recover from it. Sometimes, you will also want to log it somewhere, but then you should throw it again, so the responsibility of handling that error is forwarded to some other catch statement.  

All other unexpected errors are meant to be fixed because they should not happen, but you should know about them when they happen, and they should not fail quietly.  

> "Don't write better error messages, write code that doesn't need them." - Jason C. McDonald

Of course, there will be times when you want to throw errors on your own. However, those are expected errors, and you should know exactly how to recover from those errors. Errors like those can be used to validate user's input and be rendered on the screen to help the user know how to fix it.

### Recovery and Retry Policies

Some operations are crucially important to be executed, so the data integrity is safe. That is exactly the case where you will want to catch an **expected** error and retry it again.

For example, you have an application that needs to send a bill to the client's email address. You can only set that bill as `was_client_notified=true` if that operation works. You know that operation relies on an external service and network connectivity, so there is a considerable chance that it could go wrong. You will want to retry more times later if you could connect to the Email Server, for example. It means that you should know how to recover from that specific error, maybe by retrying it later or even switching to another Email Server option.

What if an **unexpected** error happens? Well, that is the case where you will want to [monitor and track that error](#error-monitoring-tools) so you can fix the root issue to prevent that situation from happening again. You should know what to show to your users in those scenarios, and that is where the [rendering errors](#rendering-errors) section comes in.

You should also know what part of your application is likely possible to break. For example, in a Web Application, you will likely want to break the *Request/Response* processing if an error occurs in the middle of it. So, your entire application does not shut down because of an unexpected error during a single request.

In a different scenario, if your Web Application throws an unexpected database connection error earlier during the startup of the process, you can fix the connection issue and start it again. In that case, you will want to break your application as early as possible and finish the whole process. 

### Rendering Errors

Errors are not really a good thing because they mean that something did not work as expected. You should be conscious and aware of what you want to show to your user when errors happen.  

You should explain to your user what happened with friendly words and, if possible, tell them what can be done to recover from that error. For example, if a form fails to save, you will want to show the user what fields failed and why they failed, so the user knows how to correct them to try again. On the other hand, if the application fails because of the database connection or because of a failed certificate, there is nothing the user can do but contact the person responsible for the application to delve deeper into the problem.  

Rendering errors are about trying to make a bad situation as painless as possible for the user. Your users deserve a good experience when using your application. Keep that in mind.

### Error Monitoring Tools

When an error happens, you as the developer will want to know as much detailed information as possible. Such as **Traceback**, **Browser** **(in case of web applications)**, who is the user, etc. This way, you will gather all of that information and find the root cause of the problem.

There are some monitoring tools that you can easily integrate your application with, where you will leverage some benefits of having all of that detailed information out-of-the-box.

| ![](assets/development/error-handling/rollbar.png) |
|:--:|
| *Credit: sample screenshot of the <a href="https://rollbar.com/" target="_blank">Rollbar</a> monitoring tool* |

Those monitoring tools usually come with great features like integrations with other platforms, so you can quickly pinpoint what’s broken and why as quickly as possible. For example, you can configure your monitoring tool to literally automate recovery processes like to restart failed databases. Still if you simply want to be notified, monitoring tools often have the option to make a phone call to you when a critical error occurs, or just to set it to send a chat message to you.

You can easily integrate your application with monitoring tools, leveraging the benefits of having all of that detailed information out-of-the-box.

- <a href="https://rollbar.com/" target="_blank">Rollbar</a>
- <a href="https://sentry.io/" target="_blank">Sentry</a>
- <a href="https://www.bugsnag.com/" target="_blank">Bugsnag</a>
- <a href="https://airbrake.io/" target="_blank">Airbrake</a>
- <a href="https://raygun.com/" target="_blank">Raygun</a>
