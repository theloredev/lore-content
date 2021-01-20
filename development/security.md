---
id: security
title: Security
sidebar_label: Security
---

The growing adoption of technology worldwide has brought an increase in cyber-attacks and data breaches.  To protect your application and your users, you should build your application with security as a top priority from the ground up.

## Security Threats: Knowledge Sharing

Even if you don't have expertise in application security, you can leverage existing, shared knowledge about the most common security failures in software today to make your application more secure and safer for your users.  Several reputable security experts track and explain common tactics used by hackers to compromise systems and gain unauthorized access to data. 

The two most common sources of this type of information are the <a href="https://owasp.org/www-project-top-ten/" target="_blank">Open Web Application Security Project (OWASP)</a> Top 10 and the <a href="https://us-cert.cisa.gov/ncas/current-activity/2020/08/20/2020-cwe-top-25-most-dangerous-software-weaknesses" target="_blank">Common Weakness Enumeration (CWE)</a> Top 25, led by the U.S. Department of Homeland Security.  These lists are updated yearly as the nature of cyber-attacks and data breaches is always evolving. 

In addition to reviewing reliable security threat lists that are updated daily, you should consider subscribing to a reputable daily feed or e-mail list for real-time information about emerging software threats. One of these services is offered by the <a href="https://us-cert.cisa.gov/mailing-lists-and-feeds" target="_blank">U.S. Cybersecurity and Infrastructure Security Agency (CISA)</a>. 

These types of information sources should be reviewed by your team before and during your application development—understanding how hackers try to breach systems is the first step toward building a defense against hackers.

## Hardware, Network, Operating System, Antivirus, and Anti-Malware 

As a developer, you may not be responsible for the health and quality of the hardware, network, operating system, or the antivirus and anti-malware tools your organization uses. However, you should always view yourself as a vital stakeholder with a strong interest in the quality of these components:  Your application will only be as secure as the environment in which it runs. 

Even if you do not directly control these components, you should seek to establish strong communication channels with those who do, such as your security, network, and system administration teams. Team effort is required to secure your application from the ground up. 

- Provide information to your network, security, and system administration teams about the expected functionality and needs of your application, such as:
    - Internet protocols that will be used
    - Data encodings that will be used (JSON, SOAP, etc.)
    - Special security requirements
    - Anticipated bandwidth usage or estimated number of simultaneous users
    - Estimated volume of transactions anticipated
- Sharing this type of information with your network, security, and system administration teams enables them to choose the network, hardware, and software components that support your application's security goals and to make configuration adjustments to suit the security needs of your application.
    - Remember that network security settings, firewalls, operating system patches, and security configurations, antivirus, and anti-malware all play an active role in helping secure your application from the ground up. 
- Exchanging information about your application with your network, security, and system administration teams can also prevent incorrect security configurations, which can cause your application to malfunction.

Depending on your organization, you may be asked for input in the selection process of the hardware, operating system, and antivirus and anti-malware that will host your application.  In those situations, here are a few things you should remember.

- If your organization maintains a list of preferred vendors or manufacturers, you should encourage components to be selected from that list.  
- If your organization has specifically banned some vendors or manufacturers, you should discourage their use in the selection process. The items might be banned due to known security problems. 
- Discourage the use of any hardware, antivirus, or anti-malware components that have been banned by your government or that have come under scrutiny for deliberately introducing security holes.  Here are two examples:
    - In 2017, <a href="https://www.dhs.gov/news/2017/09/13/dhs-statement-issuance-binding-operational-directive-17-01" target="_blank">the Department of Homeland Security banned the use of Kaspersky antivirus and anti-malware tools</a> on government computers, alleging the tools created system "backdoors" for international hackers, viruses, and trojan horses.  
    - Several countries, including the United States and the United Kingdom, <a href="https://www.bloomberg.com/news/features/2018-10-04/the-big-hack-how-china-used-a-tiny-chip-to-infiltrate-america-s-top-companies" target="_blank">placed bans on the use of Huawei</a>. after discovering the company's semiconductor chips created built-in system "backdoors" that allowed for international data theft.
        - This type of security hole is called a "supply chain hack" or "hardware hack" and leaves everything on the system compromised: This includes your application and the users' data.
        - Huawei chips were used worldwide in millions of smart devices, tablets, phones, computers, and servers.  

Communicating information about your application with your network, security, and system administration team is essential to secure your application. Encouraging your organization to choose trustworthy network devices, server hardware, operating systems, and antivirus and anti-malware tools can help improve your application's security from the ground up.

## Database

Most web applications and non-web applications rely on some database. If your application depends on a relational database (RDBMS) or an object database management system (ODBMS), here are a few things you can do to help secure your application from the ground up:

- If your application connects to a database, limit the level of access for the database login, the application uses for database operations to the exact permission level needed. 
    - For example, use a read-only database login if your application only needs to display data from the database. 
    - Your application should never use a database login account with administrative privileges unless it is an absolute requirement for your application.
- If your application server uses a database connection pool, you should look at the connection pool configurations that control how many failed database logins are allowed, timeouts for SQL statements, and how quickly database connections will be retried if the connection fails.
    - Simple adjustments to these configurations can help prevent malicious hackers from using your application as a tool to crash your database. Don't be afraid to work with the database administrators, system administrators, and security experts at your organization if you need advice and guidance.
- Consider using [stored procedures and stored functions with bind variables](/development/database.md#securing-your-stored-procedures-with-bind-variables) to help secure the read and write operations between your application and your database.

## Secured Applications

Here are some general rules you should follow that apply to both web applications and non-web applications:

- Don't show error messages that could reveal privileged information to the user or information about the inner-workings of your application and system
- If a login attempt fails, tell the user the login failed
    - Avoid telling the user only their username or only their password was incorrect: This level of detail helps hackers.
- Your application should not list *"maintenance window"* times that can be seen by users not currently logged into the application unless your business operations specifically require doing so.
    Hackers can use information about system downtime to target your system when it is vulnerable.
- Use automated testing and static code analysis tools that can help detect security flaws. Some examples include:
    - <a href="https://www.sonarqube.org/" target="_blank">SonarQube</a>
    - <a href="https://www.selenium.dev/" target="_blank">Selenium</a>
    - <a href="https://www.microfocus.com/en-us/solutions/application-security" target="_blank">Fortify</a>
- Consider programming your application to disable user accounts after too many failed login attempts temporarily
- Use encryption, such as SSL and HTTPS, for all communications outside your local network or Intranet.
    - You should use [well-tested third party or commercial security tools](https://docs.google.com/document/d/1OlIHaqyxohBgYRzgpjURCycFJW3F1X-77qofWevHrpw/edit#bookmark=id.h6iltuir9xci), where needed, as opposed to writing your own.
- Encrypt all passwords and <a href="https://en.wikipedia.org/wiki/Personal_data" target="_blank">Personally Identifiable Information (PII)</a>.
- Use logging extensively to help detect possible data and security breaches, record information that can be used to identify attackers, and notify appropriate personnel who can take action.
- If your application accepts any file uploads, ensure proper scanning and securing of files that are uploaded.
    - Strong antivirus and malware detection tools should be used before accepting and storing uploaded files
- When possible, try to include individuals with special security certifications or training throughout your development process to receive helpful feedback and guidance. A broad range of individuals may have these skills:
    - IT security auditors and security teams
    - Quality assurance testers specializing in security
    - Application developers with specialized security training
    - Security-certified database administrators, network engineers, and system administrators

### Non-Web Applications

For non-web applications, such as installable .exe files, you should take great care to protect distributable copies of the program and prevent them from being contaminated with viruses/malware.  You don't want to provide your users or customers with dangerous or tainted copies of your application.

- Ensure copies of your application are stored in a secure location where they cannot be modified or replaced by unauthorized people. 
- Strong antivirus and malware detection tools should be used to protect copies of your application. 
- Consider using digital signing tools, such as GnuGPG, so that users can verify they have received a valid copy of your application that has not been modified by anyone else. 

### Web Applications

When it comes to securing web applications, it is to your advantage to use up-to-date guides on the current best practices for securing web applications. New threats to web applications emerge almost daily. 

Here are some examples of guides you'll want to refer to for checklists of the potential major  problems you can help prevent: 

- <a href="https://martinfowler.com/articles/web-security-basics.html" target="_blank">The Basics of Web Application Security</a>
- <a href="https://securityledger.com/2015/10/better-web-application-security-in-14-steps/" target="_blank">Better Web Application Security in 14 Steps</a>

There are several other steps you can take to help make your web application as secure as possible:

- If possible, configure your web server or application server to stop sending HTTP headers that identify the server's vendor and version. This information is useful for hackers who can use server vendor and version information to fine-tune an attack on your system.
    - <a href="https://www.acunetix.com/blog/articles/configure-web-server-disclose-identity/" target="_blank">Configuring Your Web Server to Not Disclose Its Identity</a>
- Protect access to the directories on your web server or application server
    - For instance, a web surfer going to a URL on your server at **http://your-host/pictures/home.asp** should not be able to change the link address in their web browser to **http://your-host/pictures/** and view all the files in the **/pictures/** directory.
- Protect your application's APIs and web services so they can't be invoked outside your application unless necessary.
    - If outside access by select groups or individuals is essential, consider limiting that access by using firewalls, site certificates, and authentication. 
- Consider deploying a Web Application Firewall to protect your application.
    - *"A WAF or Web Application Firewall helps protect web applications by filtering and monitoring HTTP traffic between a web application and the Internet. It typically protects web applications from attacks such as cross-site forgery, cross-site-scripting (XSS), file inclusion, and SQL injection, among others." - <a href="https://www.cloudflare.com/learning/ddos/glossary/web-application-firewall-waf/#:~:text=A%20WAF%20or%20Web%20Application,and%20SQL%20injection%2C%20among%20others." target="_blank">WAF Learning Objectives</a>*
    - A Web Application Firewall can be used to help secure your application's APIs and web services.

## Logging and Notifications

Useful logging throughout all layers of your application can help increase the overall security of your application. Well-configured logging can be used to alert you, and your colleagues of potential security breaches and help provide information about the root cause of the security breach. 

The two primary ways of storing security log information are through a file system or a database.  Regardless of whether you select a file system or a database for storing your application's security logs, there are general rules you should follow to help secure the logs themselves. If a security breach is severe enough, even the security logs could be lost or corrupted if not adequately secured.

Suppose you choose to implement security logging using a file system. In that case, OWASP recommends that you *"use a separate partition than those used by the operating system, other application files, and user-generated content."* You should also *"apply strict permissions concerning which users can access the directories, and the permissions of files within the directories"* - <a href="https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html" target="_blank">OWASP Logging Cheat Sheet</a>  

If you choose a database as your means of storing security-related log information, you must take special care to safeguard the database itself. Ideally, you will want to *"utilize a separate database account that is only used for writing log data and which has a very restrictive database, table, function, and command permissions."* - <a href="https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html" target="_blank">OWASP Logging Cheat Sheet</a>   

No matter which method you choose for storing security logs, it is always a good idea to store the logs on more than one device, whenever possible. Security logs stored in your local database could also be replicated to another database within your network, a cloud-based database, or a file share on another machine or network.

Consider using security logging throughout all layers of your application and the systems your application touches:

- Application or code-level logging of errors or other events of interest
- Web application logging
- Database logging
- Operating system-level logging, such as the Windows Event Manager or Syslog
- Network and firewall level logging

Security logging throughout your application and all the systems your application touches can provide you with an early warning regarding possible security breaches and useful information to determine the source of a security breach should one occur. 

Here are just a few examples of events within your application that could indicate a security breach and should be logged:

- Failed login attempts, especially multiple failed login attempts
- Failed database login attempts originating from your application
- Invalid URL requests to your application or application server
- Invalid or malformed packets or messages sent to any web services or APIs
- Invalid form data sent to your application
- Application errors, runtime errors, performance issues, and connectivity issues which could indicate a security breach is underway

The quality of the information stored in your security logs is also critical. You'll want to make sure you collect all information that could be used to identify the source and nature of any security breach. 

The first pieces of information you should always log are the event date and time, the severity of the event, and the particular action performed within your application when the event occurred. OWASP also recommends logging the following additional information:

**Where**
- Application identifier e.g. name and version
- Application address e.g. cluster/hostname or server IPv4 or IPv6 address and port number, workstation identity, local device identifier
- Service e.g. name and protocol
- Geolocation
- Window/form/page e.g. entry point URL and HTTP method for a web application, dialogue box name
- Code location e.g. script name, module name

**Who (human or machine user)**
- Source address e.g. user's device/machine identifier, user's IP address, cell/RF tower ID, mobile telephone number
- User identity (if authenticated or otherwise known) e.g. user database table primary key value, user name, license number" - <a href="https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html" target="_blank">OWASP Logging Cheat Sheet</a>  

Large quantities of logs containing so much information could become unmanageable, especially for a large system. Consider using a centralized logging and event management system designed for this purpose. A few options include:
- <a href="https://www.solarwinds.com/" target="_blank">SolarWinds</a>
- <a href="https://www.splunk.com/" target="_blank">Splunk</a>
- <a href="https://www.datadoghq.com/" target="_blank">DataDog</a>

Many web application servers and centralized logging and event management systems offer the ability to send notifications when certain security-related events occur. Consider implementing e-mail, phone, or text notifications for specific events captured in your security logs to alert yourself or other team members when a possible security breach is underway.

## References
- <a href="https://owasp.org/www-project-top-ten/" target="_blank"><https://owasp.org/www-project-top-ten/></a>
- <a href="https://us-cert.cisa.gov/ncas/current-activity/2020/08/20/2020-cwe-top-25-most-dangerous-software-weaknesses" target="_blank"><https://us-cert.cisa.gov/ncas/current-activity/2020/08/20/2020-cwe-top-25-most-dangerous-software-weaknesses></a>
- <a href="https://us-cert.cisa.gov/mailing-lists-and-feeds" target="_blank"><https://us-cert.cisa.gov/mailing-lists-and-feeds></a>
- <a href="https://www.bloomberg.com/news/features/2018-10-04/the-big-hack-how-china-used-a-tiny-chip-to-infiltrate-america-s-top-companies" target="_blank"><https://www.bloomberg.com/news/features/2018-10-04/the-big-hack-how-china-used-a-tiny-chip-to-infiltrate-america-s-top-companies></a>
- <a href="https://www.dhs.gov/news/2017/09/13/dhs-statement-issuance-binding-operational-directive-17-01" target="_blank"><https://www.dhs.gov/news/2017/09/13/dhs-statement-issuance-binding-operational-directive-17-01></a>
- <a href="https://gnupg.org/" target="_blank"><https://gnupg.org/></a>
- <a href="https://en.wikipedia.org/wiki/Personal_data" target="_blank"><https://en.wikipedia.org/wiki/Personal_data></a>
- <a href="https://www.microfocus.com/en-us/solutions/application-security" target="_blank"><https://www.microfocus.com/en-us/solutions/application-security></a>
- <a href="https://www.selenium.dev/" target="_blank"><https://www.selenium.dev/></a>
- <a href="https://www.sonarqube.org/" target="_blank"><https://www.sonarqube.org/></a>
- <a href="https://martinfowler.com/articles/web-security-basics.html" target="_blank"><https://martinfowler.com/articles/web-security-basics.html></a>
- <a href="https://www.cloudflare.com/learning/ddos/glossary/web-application-firewall-waf/#:~:text=A%20WAF%20or%20Web%20Application,and%20SQL%20injection%2C%20among%20others." target="_blank"><https://www.cloudflare.com/learning/ddos/glossary/web-application-firewall-waf/#:~:text=A%20WAF%20or%20Web%20Application,and%20SQL%20injection%2C%20among%20others.></a>
- <a href="https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html" target="_blank"><https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html></a>
- <a href="https://www.solarwinds.com/" target="_blank"><https://www.solarwinds.com/></a>
- <a href="https://www.splunk.com/" target="_blank"><https://www.splunk.com/></a>
- <a href="https://www.datadoghq.com/" target="_blank"><https://www.datadoghq.com/></a>
