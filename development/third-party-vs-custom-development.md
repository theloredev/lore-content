---
id: third-party-vs-custom-development
title: Third-party vs. Custom Development
sidebar_label: Third-party vs. Custom Development
---

Let's look at how to determine when third-party libraries, APIs, and web services are a better option over custom development from scratch.  Third-party libraries, APIs, and web services can significantly accelerate your application's completion and offer multiple benefits. Still, they can introduce some risks and may not fit all situations and projects.

## Possible benefits of third-party

### Save development time

A third-party library, API, or web service that provides the functionality required but is also easy to learn and integrate into your application can save hours, days, or even weeks of development time.

### Save money

Thousands of stable, tested, and free-of-charge third-party libraries and APIs are available to assist you with completing your application.

Many such libraries and APIs are available under Open Source licenses, such as the [GNU General Public License](https://opensource.org/licenses/GPL-3.0), the <a href="https://opensource.org/licenses/BSD-3-Clause" target="_blank">BSD License</a>, and the <a href="https://opensource.org/licenses/Apache-2.0" target="_blank">Apache License</a>, which offer very generous rights to use, modify, and redistribute the software.

As an example, <a href="https://projects.apache.org/projects.html?category" target="_blank">Apache</a>  maintains an extensive collection of third-party Open Source libraries and APIs.

Another example is the Python Package Index <a href="https://pypi.org" target="_blank">(PyPi)</a>.  

### Improvements to your application's stability and security

Your team can avoid introducing unwanted bugs and security flaws that are likely to occur when coding common, complex functionality from scratch.

See <a href="http://abstractedge.com/open-source-vs-build-your-own-software/" target="_blank">Open source vs Build your own software</a>.

Example scenario:

If your application needs the functionality to handle encrypted authentication and process occasional PDF files. The completion of your application as a whole can become side-tracked and delayed if the development team devotes extensive time to developing and debugging encryption algorithms and PDF rendering functionality from scratch. 

Your application might also benefit from long-term stability and security of well-tested third-party libraries, APIs, and web services. They can be well-maintained by their original author or vendor with frequent bug fix releases.

You should research the release history of any third-party libraries, APIs, and web services under consideration for inclusion.

A well-tested and well-maintained third-party component will have been in active development for several years with frequent software releases that include bug fixes and other improvements.

As an example, take a look at the extensive release history for the open-source <a href="https://imagemagick.org/script/changelog.php" target="_blank">ImageMagick</a> library. 

### Possible reduced application maintenance when using third-party

Utilizing a stable, well-tested web service maintained by a third-party means your team does not have to devote time and effort to maintaining and repairing that portion of your application. 

## Risks associated with using third-party

### Possible future changes in cost or price

This risk is specific to many commercial and proprietary solutions and some cloud-based and web services that may require the payment of licensing fees, maintenance fees, bandwidth fees, or usage fees.

### A third-party component may become unmaintained

This risk is particularly prevalent with Open Source libraries and APIs. Most Open Source licenses stipulate the author(s) has no legal obligation to provide future bug fixes or updates to their software.

### Possible lack of warranty or technical support

Many third-party components are offered as-is, without any warranty or technical support available.

Some third-party components may offer a warranty or technical support options, but for an added fee under a separate licensing agreement. 

### Sudden changes of third-party

Sudden changes to third-party libraries, APIs, or web services may introduce new bugs in your application or cripple your application entirely in the future.

This risk is much lower for libraries and APIs because your team controls when and if new versions of third-party libraries and APIs are integrated into your application.

If a new version of a library or API is determined to be incompatible with your application, the team can choose not to use the new version.

Sudden changes to web services controlled by a third-party can cause major bugs within your application or cripple your application completely. 

For example, a third-party web service may initially accept and send messages in an XML format your application expects. 

If that web service is suddenly modified to accept and send messages in JSON format only, major features within your application or the entire application itself may stop functioning properly.

### Security vulnerabilities of third-party

Third-party libraries, APIs, and web services may add security vulnerabilities to your application.

This risk is lower for libraries and APIs because your team can perform its own security assessment of the library or API before including it in the application.

Extensive research, manual code review, manual testing, and automated testing of the library or API are some methods that can be used to prevent this risk. 

Third-party web services create a greater risk of introducing security vulnerabilities into your application, especially if the web service is publicly-accessible or not properly secured.

Security holes allowing remote code execution, remote command execution, malicious code injection, and sensitive information exposure are just a few of the risks third-party web services may introduce into your application. 

See <a href="https://blog.radware.com/security/2020/04/top-10-web-service-exploits-in-2019/" target="_blank">Top 10 Web Service Exploits in 2019</a>.

## Considerations when deciding whether to build/buy or build/borrow

### Security requirements

For example, many government agencies and private corporations releasing proprietary software have strict limitations on what portions of your software may be released to the public.  Many open-source licenses require you to publicly release any modifications to the original author's source code as a condition of utilizing the open-source software library. 
 
This clause in many Open Source licenses can create problems for organizations that operate under highly confidential levels. 
 
Licensing problems from third-party libraries, APIs, and services  can create problems for the following entities:

- Government agencies with classified, confidential, medical, financial, or personally identifiable information (<a href="https://www.gsa.gov/reference/gsa-privacy-program/rules-and-policies-protecting-pii-privacy-act" target="_blank">PII</a>)
- Private companies who hold proprietary patents or handle sensitive medical, confidential, financial, or personally identifiable information (<a href="https://www.gsa.gov/reference/gsa-privacy-program/rules-and-policies-protecting-pii-privacy-act" target="_blank">PII</a>)

See <a href="https://www.gsa.gov/reference/gsa-privacy-program/rules-and-policies-protecting-pii-privacy-act" target="_blank">Rules and policies protecting PII  privacy act></a>.

Until recently, much of the Federal U.S. government remained opposed to leveraging Open Source software for their development needs. Attitudes within the U.S. government have changed in many agencies, who not only embrace the use of Open Source but encourage the Open Source distribution of government-developed software programs:  
 
However, the U.S. government, like many other organizations, <a href="https://sourcecode.cio.gov/Exceptions/" target="_blank">have limits on what software modifications may be released publicly</a> in compliance with Open Source licensing agreements.

### Software costs

Maintenance and usage fees. For example, the use of certain third-party services and APIs can be subject to unexpected changes in prices and licensing costs in the future. 
 
Some examples include <a href="https://www.twilio.com/" target="_blank">Twilio</a> and <a href="https://aws.amazon.com/" target="_blank">AWS</a>.

### Software licensing

Suppose your program or organization intends to release software under proprietary license agreements. In that case, there is a great possibility that the licensing terms of some Open Source licenses may conflict with the license under which you intend to release your software or web application. 

### Stability, maintenance, and availability of Third-party

Suppose you are using an old or legacy language. There is a high possibility that you will be unable to find third-party libraries and services for the functionality you are seeking due to a lack of active developers utilizing the language.

Similarly, suppose you are using a new, "cutting edge" programming language that has been in existence for less than 1-2 years. You will likely experience problems locating third-party libraries for your language due to a lack of developers working on extended functionality for that language. 

#### Learning curve

Is the software library too difficult or confusing to use?  If your team's learning curve to understand how to leverage the third-party software outweighs the benefits, using the third-party component is probably not worth the trouble.

#### Long-Term-Support

Suppose the third-party library, API, or service suddenly goes into an "unmaintained" status. Are you and your team willing to make the upgrades and bug fixes necessary to keep your application's component functional? If you are not, then you may want to avoid using that particular third-party component.

Particularly, with Open Source software, the author(s) have no legal obligation to maintain or fix issues for the software in the future. Your team could be on their own if the third-party software library, API, or service becomes abandoned in the future. 

### Organizational approval

How difficult is getting the third-party component approved for use by your organization?

Whether you come from the government or private industry, "red tape" is a fact of life in the world of IT. Before considering introducing a third-party library, API, or web service, you may wish to consider the time and effort you may have to exhaust to gain approval from your management, company, or organization to begin utilizing the new third-party component. 

If the time and effort to gain organizational approval for the use of the third-party component outweighs the benefits of using the component, it may not be worth. 

Suppose your team can build similar functionality in two weeks, but getting approval to use a third-party component may take you 4-5 months. You may be better off letting your team build the component in the interest of saving time, money, and unnecessary frustration. 

## Examples of functionality best fit to be fulfilled with third-party libraries, APIs, or web services 

Common functionalities are likely to have been required/developed by other developers in the past. They might not be your application's focal point, and in that case, it would be beneficial to them to speed up your application's development. 

### Time zones

Date/time functionality, such as calculating Time Zone differences.

As an example, the following well-used library provides this type of functionality: 

- <a href="http://pytz.sourceforge.net/" target="_blank">PyTZ</a> -  World Timezone Definitions for Python

### Data formats

Reading, editing, saving, rendering, or parsing popular document and data formats, such as XML, JSON, MS documents, PDF, JSON, and CSV.

Several well-tested, Open Source libraries are available to assist with the rendering and processing of these types of documents. A few examples include:

- <a href="https://pdfbox.apache.org/" target="_blank">Apache PDFBox</a> (PDF Processing) 
- <a href="https://xerces.apache.org/" target="_blank">Apache Xerces</a> (XML Processing)
- <a href="https://commons.apache.org/proper/commons-csv/" target="_blank">Apache Commons CSV</a> (CSV processing)

Many well-tested, Open Source libraries are available to assist with reading, editing, playback, or the rendering of popular media or image formats, such as MP4, AVI, MP3, WAV, PNG, SVG, JPEG, GIF, or OGG. A few examples include the following:

- <a href="https://imagemagick.org/script/magick++.php" target="_blank">ImageMagick</a> (Image rendering, editing, and conversion)
- <a href="https://ffmpeg.org/documentation.html" target="_blank">FFMPEG API</a> (Video rendering, editing, and conversion)

### Internacionalization

Commonly used language tools and features: dictionaries, thesauri, spell check, grammar check, and language translation.

One such example includes the <a href="https://github.com/googleapis/java-translate" target="_blank">Google Language Translation API</a>.

### Mailing & Texting

Advanced email functionality, like handling file attachments and email groups and synching messages or sending SMS text messages to mobile phones. A few available options to help you accomplish these types of tasks are readily available, including the following options:

- <a href="https://www.nylas.com/products/email-api/" target="_blank">Nylas</a>
- <a href="https://www.twilio.com/" target="_blank">Twilio</a>

### Tooling

Features or functionality within the program that will only be used by the developers or other IT support personnel, not customers or end users.

One such example includes the popular Open Source <a href="https://logging.apache.org/log4j/2.x/" target="_blank">LOG4J</a> library by Apache, which provides very advanced, centralized logging features to files and database tables to aid the efforts of developers in troubleshooting and debugging their applications.

### Security

Security features such as encryption or password rule enforcement. 

One such example includes <a href="https://www.npmjs.com/package/crypto-js" target="_blank">crypto-JS</a>.

Unless your company or organization operates in the cybersecurity space, encryption algorithms are better left to the experts in that field.

Attempting to implement new encryption mechanisms and algorithms from scratch and on your own creates the added risk of unexpected bugs and security flaws within your application.

The well-developed, well-tested, tried, and true encryption libraries will normally be the best options for your program or web application.

### Third-party data

Functionality that relies on real-time data generated by private organizations. As an example, shipping rates for USPS and FedEx, which could change at any moment.

These companies will know before anyone else when rates have changed and offer APIs and web services available to developers to supply the most recent shipping and freight rates.

Some examples include the following available web services: 

- <a href="https://www.fedex.com/en-us/developer/web-services.html" target="_blank">FedEx</a>  
- <a href="https://www.usps.com/business/web-tools-apis/" target="_blank">USPS</a>  

### Proprietary vendors

Critical features are only available from proprietary vendors such as an API or Web Service provided by the manufacturer of a commercial, patented medical device, financial information system, or robotic device.

## References

- <a href="https://www.cmu.edu/tcinc/students/course_documents/08/BuyBuild.pdf" target="_blank">"Build / Buy"</a>, Carnegie Mellon University
- <a href="http://abstractedge.com/open-source-vs-build-your-own-software/" target="_blank">"Open Source vs. Build-Your-Own Software"</a>, Scott Paley
- <a href="https://blog.radware.com/security/2020/04/top-10-web-service-exploits-in-2019/" target="_blank">"Top 10 Web Service Exploits in 2019"</a>, Radware Vulnerability Research Team
