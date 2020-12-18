---
id: third-party-vs-custom-development
title: Third-party vs. Custom Development
sidebar_label: Third-party vs. Custom Development
---

Let's look at how  to determine when third-party libraries, APIs, and web services are a better option over custom development from scratch.  Third-party libraries, APIs, and web services can greatly accelerate the completion of your application and offer multiple benefits, but may also introduce some risks and may not be a fit for all situations and projects.

## Possible benefits of third-party

### Save development time

A third-party library, API, or web service that provides the functionality required but is also easy to learn and integrate into your application can save hours, days, or even weeks of development time.

### Save money

Thousands of stable, tested, and  free-of-charge third party libraries and APIs are available to assist you with completing your application.

Many such libraries and APIs are available under Open Source licenses, such as the [GNU General Public License](https://opensource.org/licenses/GPL-3.0), the [BSD License](https://opensource.org/licenses/BSD-3-Clause), and the [Apache License](https://opensource.org/licenses/Apache-2.0), which offer very generous rights to use, modify, and redistribute the software.

As an example, Apache maintains a large collection of third-party Open Source libraries and APIs: <https://projects.apache.org/projects.html?category>

Another example is the Python Package Index (PyPi): <https://pypi.org>

### Improvements to your application's stability and security

Your team can avoid introducing unwanted bugs and security flaws that are likely to occur when coding common, complex functionality from scratch.

See <http://abstractedge.com/open-source-vs-build-your-own-software/>.

Example scenario:

If your application needs functionality to handle encrypted authentication and process occasional PDF files, the completion of your own application as a whole can become side-tracked and delayed if the development team devotes extensive time to developing and debugging encryption algorithms and PDF rendering functionality from scratch. 

Your application might also benefit long-term from the added stability and security well-tested third-party libraries, APIs, and web services offer if they are well-maintained by their original author or vendor with frequent bug fix releases offered.

You should research the release history of any third-party libraries, APIs, and web services under consideration for inclusion.

A well-tested and well-maintained third-party component will have been in active development for a number of years with frequent software releases that include bug fixes and other improvements.

As an example, take a look at the extensive release history for the open source ImageMagick library: <https://imagemagick.org/script/changelog.php>

### Possible reduced application maintenance when using third-party

Utilizing a stable, well-tested web service maintained by a third-party means your team does not have to devote time and effort to maintaining and repairing that portion of your application. 

## Risks associated with using third-party

### Possible future changes in cost or price

This risk is specific to many commercial and proprietary solutions as well as some cloud-based and web services which may require the payment of licensing fees, maintenance fees, bandwidth fees, or usage fees.

### A third-party component may become unmaintained

This risk is particularly prevalent with Open Source libraries and APIs, since most Open Source licenses stipulate the author(s) has no legal obligation to provide future big fixes or updates to their software.

### Possible lack of warranty or technical support

Many third-party components are offered as-is, without any warranty or technical support available.

Some third-party components may offer a warranty or technical support options, but for an added fee under a separate licensing agreement. 

### Sudden changes of third-party

Sudden changes to third-party libraries, APIs, or web services may introduce new bugs in your application or cripple your application completely in the future.

This risk is much lower for libraries and APIs because your team controls when and if new versions of third-party libraries and APIs are integrated into your application.

If a new version of a library or API is determined to be incompatible with your application, the team can choose not to use the new version.

Sudden changes to web services controlled by a third-party can cause major bugs within your application or cripple you application completely. 

As an example, a third-party web service may initially accept and send messages in a XML format your application expects. 

If that web service is suddenly modified to accept and send messages in JSON format only, major features within your application or the entire application itself may stop functioning properly.

### Security vulnerabilities of third-party

Third-party libraries, APIs, and web services may add security vulnerabilities to your application.

This risk is lower for libraries and APIs because your team can perform its own security assessment of the library or API before including it in the application.

Extensive research, manual code review, manual testing, and automated testing of the library or API are some methods that can be used to prevent this risk. 

Third-party web services create a greater risk of introducing security vulnerabilities into your application, especially if the web service is publicly-accessible or not properly secured.

Security holes allowing remote code execution, remote command execution, malicious code injection, and exposure of sensitive information are just a few of the risks third-party web services may introduce into your application. 

See [Top 10 Web Service Exploits in 2019](https://blog.radware.com/security/2020/04/top-10-web-service-exploits-in-2019/).

## Considerations when deciding whether to build/buy or build/borrow

### Security requirements

For example, many government agencies and private corporations releasing proprietary software have strict limitations on what portions of your software may be released to the public.  Many open source licenses require you to publicly release any modifications to the original author's source code as a condition of utilizing the open source software library. 
 
This clause in many Open Source licenses can create problems for organizations which operate under highly confidential levels. 
 
Licensing problems from third-party libraries, APIs, and services  can create problems for the following entities:

- Government agencies with classified, confidential, medical, financial, or personally identifiable information ([PII](https://www.gsa.gov/reference/gsa-privacy-program/rules-and-policies-protecting-pii-privacy-act))
- Private companies who hold proprietary patents or handle sensitive medical, confidential, financial, or personally identifiable information ([PII](https://www.gsa.gov/reference/gsa-privacy-program/rules-and-policies-protecting-pii-privacy-act))

See <https://www.gsa.gov/reference/gsa-privacy-program/rules-and-policies-protecting-pii-privacy-act>.

Until recently, much of the Federal U.S. government remained opposed to leveraging Open Source software for their development needs. Attitudes within the U.S. government have changed in many agencies, who not only embrace the use of Open Source, but encourage the Open Source distribution of government-developed software programs:  
 
However, the U.S. government, like many other organizations, have limits on what software modifications may be released publicly in compliance with Open Source licensing agreements: <https://sourcecode.cio.gov/Exceptions/>

### Software costs

Including any maintenance and usage fees. For example, use of certain third-party services and API's can be subject to unexpected changes in fees and licensing costs in the future. 
 
Some examples include [Twilio](https://www.twilio.com/) and [AWS](https://aws.amazon.com/).

### Software licensing

If your program or organization intends to release software under proprietary license agreements, there is a great possibility that the licensing terms of some Open Source licenses may conflict with the license under which you intend to release your software or web application. 

### Stability, maintenance and availability of Third-party

The stability, maintenance, and availability of  3rd party libraries for the language(s) you are using.

If you are using an old or legacy language, there is a high possibility that you will be unable to find third-party libraries and services for the functionality you are seeking due to a lack of active developers utilizing the language.

Similarly, if you are using a new, "cutting edge" programming language that has been in existence for less than 1-2 years, you will likely experience problems locating third-party libraries for your language due to a lack of developers working on extended functionality for that language. 

#### Learning curve

Is the software library too difficult or confusing to use?  If the learning curve of your team understanding how to leverage the third-party software outweighs the benefits, then using the third-party component is probably not worth the trouble.

#### Long-Term-Support

If the third-party library, API, or service suddenly goes into an "unmaintained" status, are you and your team willing to make the upgrades and bug fixes necessary to keep the component functional for your application? If you are not, then you may want to avoid using that particular third-party component.

Particularly, with Open Source software, the author(s) have no legal obligation to maintain or fix issues for the software in the future, which means your team could be on their own if the third-party software library, API, or service becomes abandoned in the future. 

### Organizational approval

How difficult is getting the third-party component approved for use by your organization?

Whether you come from government or private industry, "red tape" is a fact of life in the world of IT. Before considering the introduction of a third-party library, API, or web service, you may wish to consider the time and effort you may have to exhaust to gain approval from your management, company, or organization to begin utilizing the new third-party component. 

If the time and effort to gain organizational approval for use of the third-party component outweighs the benefits of using the component, it may not be worth your while. 

As an example, if your team can build similar functionality in 2 weeks, but getting approval to use a third-party component may take you 4-5 months, you may be better off letting your team build the component in the interest of saving time, money, and unnecessary frustration. 

## Examples of functionality best fit to be fulfilled with 3rd party libraries, APIs, or web services 

A common functionality likely to have been required by other developers in the past and present but functionality which may not be the primary focal point of the application you are developing.

### Time zones

Date/time functionality, such as calculating Time Zone differences.

As an example, the following well-used library provides this type of functionality: 

- [PyTZ](http://pytz.sourceforge.net/) -  World Timezone Definitions for Python

### Data formats

Reading, editing, saving, rendering, or parsing of popular document and data formats, such as XML, JSON, MS documents, PDF, JSON, and CSV.

A number of well-tested, Open Source libraries are available to assist with rendering and processing of these types of documents. A few examples include:

- [Apache PDFBox](https://pdfbox.apache.org/) (PDF Processing)
- [Apache Xerces](https://xerces.apache.org/) (XML Processing)
- [Apache Commons CSV](https://commons.apache.org/proper/commons-csv/) (CSV processing)

Reading, editing, playback, or rendering of popular media or image formats, such as MP4, AVI, MP3, WAV, PNG, SVG, JPEG, GIF or OGG.

A number of  well-tested, Open Source libraries are available to assist with rendering and processing of these popular media and image formats. A few examples include the following:

- [ImageMagick](https://imagemagick.org/script/magick++.php) (Image rendering, editing, and conversion)
- [FFMPEG API](https://ffmpeg.org/documentation.html) (Video rendering, editing, and conversion)

### Internacionalization

Commonly used language tools and features: dictionaries, thesauri, spell check, grammar check, and language translation.

One such example includes the [Google Language Translation API](https://github.com/googleapis/java-translate).

### Mailing & Texting

Advanced email functionality, like handling of file attachments and email groups and synching messages or sending SMS text messages to mobile phones. A few available options to help you accomplish these types of tasks are readily available, including the following options:

- [Nylas](https://www.nylas.com/products/email-api/)
- [Twilio](https://www.twilio.com/)

### Tooling

Features or functionality within the program that will only be used by the developers or other IT support personnel, not customers or end users.

One such example includes the popular Open Source [LOG4J](https://logging.apache.org/log4j/2.x/) library by Apache which provides very advanced, centralized logging features to files and database tables to aid the efforts of developers in troubleshooting and debugging their applications.

### Security

Security features such as encryption or password rule enforcement. 

One such example includes [crypto-JS](https://www.npmjs.com/package/crypto-js).

Unless your company or organization operates in the cyber security space, encryption algorithms are better left to the experts in that field.

Attempting to implement new encryption mechanisms and algorithms, from scratch and on your own, creates the added risk of unexpected bugs and security flaws within your application.

The well-developed, well-tested, tried and true encryption libraries will normally be the best options for your program or web application.

### Third-party data

Functionality that relies on real-time data generated by private organizations. As an example, shipping rates for USPS and FedEx which could change at any moment.

These companies will know before anyone else when rates have changed and offer APIs and web services available to developers that will supply the most recent shipping and freight rates.

Some examples include the following available web services: 

- [FedEx](https://www.fedex.com/en-us/developer/web-services.html)
- [USPS](https://www.usps.com/business/web-tools-apis/)

### Proprietary vendors

Critical features that are only available from proprietary vendors such as an API or Web Service provided by the manufacturer of a commercial, patented medical device, financial information system, or robotic device.

## References

- ["Build / Buy"](https://www.cmu.edu/tcinc/students/course_documents/08/BuyBuild.pdf), Carnegie Mellon University
- ["Open Source vs. Build-Your-Own Software"](http://abstractedge.com/open-source-vs-build-your-own-software/), Scott Paley
- ["Top 10 Web Service Exploits in 2019"](https://blog.radware.com/security/2020/04/top-10-web-service-exploits-in-2019/), Radware Vulnerability Research Team
