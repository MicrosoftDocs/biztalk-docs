---
title: "Automating the Build Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 995dac20-82a1-46ed-b8a3-0aa6182cb821
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Automating the Build Process
An automated build process compiles, deploys and then runs build verification tests (BVTs) against the latest source code for a project at regular, predetermined intervals. Then a “build report,” which details the success or failure of the build process, is disseminated to the project stakeholders. The build report is analyzed to determine what areas of the project need attention and if the project should be rolled back to an earlier version/build.  
  
 The power of an automated build process is that it can be scheduled to be run during “off hours.” This way, it can help ensure the stability of the project without taking cycles directly away from the development time.   
 This topic provides an overview of the build process, describes how build verification testing fits into the build process, describes aspects of functional testing used during build verification testing and provides information about the importance of automating the build process.  
  
## Overview of the build process  
 Before looking into the specifics of testing, it’s important to consider the context of how testing fits into the overall build process. All of Microsoft’s product groups operate from the philosophy that the build process is the heartbeat of any software project. This approach is also used by many of the world’s top consulting firms that build mission-critical solutions on top of the Microsoft software stack. Without a steady heartbeat and a regular check of it, it is impossible to know the health of the project. To ensure that the product groups have a continuous insight into the overall health of the project, the build process is run daily, typically at midnight. The following steps summarize a typical automated build process:  
  
1.  Obtain the latest build of source code from the source code repository.  
  
2.  Compile the source code.  
  
3.  Pack up binaries for deployment – typically using scripts or Microsoft Windows Installer files.  
  
4.  Deploy project to a test server.  
  
5.  Automatically run a full set of build verification tests (BVTs).  
  
6.  Publish a detailed build report to members of the project team.  
  
> [!NOTE]  
>  BVTs are functional tests that exercise the main features of the solution to test its quality.  You need to ensure your BVTs are comprehensive enough to gauge the build quality, yet small enough to execute within the allocated daily build time!  
  
> [!NOTE]  
>  You should also treat any deployment, un-deployment, configuration and installation scripts or processes as part of the software project for testing purposes. Both the operations of the project, as well as the deployment and configuration of it, should be tested.  
  
 This process is typically completed by early morning around 6 A.M., which enables the first members of the team to start work on the new day’s build. If one or more of the BVTs from the previous night failed, then it is the team’s responsibility to fix it as soon as possible.  
  
 Following a daily build process has many advantages for the project. First, it provides a regular heartbeat (made up of the daily build plus the automated BVTs). Second, using BVTs forces integration with systems which is a tricky task, and doing this early in and of itself reduces project risks. Due to the time required to complete them, stress and performance testing are typically performed outside of the daily build process. Stress and performance tests are typically scheduled to be performed on a milestone build in the project.  
  
 The daily build process can be, and has been used, very effectively on BizTalk solutions. However, you need to ensure tasks that are typically left to the end in projects are done iteratively from the start. For example, deployment in BizTalk Server is certainly non-trivial. It is important that automated deployment scripts be developed up front. If you do not do this, you’ll end up manually deploying and un-deploying the solution many times throughout the project, which will cost you more time in the end. There are tools available to drive the daily build process; Visual Studio Team System and Team Foundation Server are the primary choice for many people. MSBuild scripts may be used to drive the steps in the build process. Another alternative is the open source [CruiseControl.NET tool](http://go.microsoft.com/fwlink/?LinkId=116093) (http://go.microsoft.com/fwlink/?LinkId=116093).  
  
> [!NOTE]  
>  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.  
  
 For more information about automating testing using Microsoft Test manager, see the topic [Running Automated Tests](http://go.microsoft.com/fwlink/?LinkID=208368) (http://go.microsoft.com/fwlink/?LinkID=208368)  in the Visual Studio 2010 online documentation  
  
 For more information about automating the build process using Visual Studio 2010, see [Building the Application](http://go.microsoft.com/fwlink/?LinkID=208369) ( HYPERLINK "<http://go.microsoft.com/fwlink/?LinkID=208369>" <http://go.microsoft.com/fwlink/?LinkID=208369>)  in the Visual Studio 2010 documentation.  
  
## Build verification testing  
 Build verification testing usually comprises the following elements:  
  
- **Unit Tests** - Because unit tests are typically the first tests to be developed, ideally they should be created before the code has actually been written, if you are truly using a test-driven development approach. By adding them into BVTs during the early stages of a project, you provide at least some code coverage immediately. As the number of functional tests and hence test coverage grows, you may opt to remove unit tests from the BVTs.  
  
- **Smoke Tests** - End-to-end functional tests that test the basic functionality of your solution. If these fail, something is seriously wrong. These can usually be run relatively quickly.  
  
- **Functional Tests** - These also target end-to-end scenarios, but in this case they test all the scenarios in the project. For large projects it may make sense to categorize your functional tests further (for instance, to enable a particular component to be tested quickly, reliably, and in isolation). These functional tests should be locked down after you have signed off on your solution as being functionally correct.  
  
- **Regression Verification Tests** - Every time a solution bug is found and fixed, regression verification test cases should be added to verify that the bug is fixed and that it is not reintroduced later in the project life cycle.  These tests will typically be cases that were not covered in the functional test cases. You should expect that your regression verification tests will increase in number even after the solution has gone live, if new bugs are discovered and fixed.  
  
  On very large projects, you may need to make your BVTs a subset of the full functional test suite (due to length of time they take to execute). For smaller projects, BVTs will constitute the entire set. Obviously, if you are going to integrate the BVTs as part of your daily build, the whole process needs to be automated. In the rest of this topic, we will focus on how you can use BizUnit and other tools to accomplish this.  
  
## Functional testing  
 In the context of BizTalk applications functional tests, test a specific end-to-end scenario. When performing this type of testing, it is useful to imagine BizTalk Server as a black box that you test functionally from an external perspective. For example, a test may involve feeding an input message (with known values) to a receive location end point (for example, URL, FTP location, whatever your choice of transport is). The test would then monitor the correct number of messages with the correct output that is produced on the send side. This may sound relatively straightforward. However, when you consider that some scenarios require inputs to come in a certain order and at a certain time, and you compound this with other solution requirements (such as, when recording tracking data in BAM), it becomes clear that a tool and framework can be used to orchestrate this.  
  
 It is critical that functional testing is designed to cover all the possible paths through your solution. This should include not only those scenarios you expect in production, but also the failure paths and exception handling paths you have implemented but hope never to use – one phrase commonly used to describe this is testing for the “bad day scenario.” You should ensure all orchestrations, all permissible message types, and all code branches are exercised by your functional test suite. The following sections describe developing positive and negative functional test cases to cover all code paths.  
  
 For more information about functional testing and the other testing categories that should be implemented before placing a BizTalk Server solution into production, see the topic [Checklist: Testing Operational Readiness](http://go.microsoft.com/fwlink/?LinkId=160138) in the BizTalk Server 2010 Operations Guide at [http://go.microsoft.com/fwlink/?LinkId=160138](http://go.microsoft.com/fwlink/?LinkId=160138).  
  
### Positive tests  
  
-   It is important when performing positive tests to ensure all combinations of messages, pipelines, orchestrations, and endpoints are passed through the solution so that all the message flows are exercised. To ensure that you test all code paths will likely require that you process different messages with different content.  
  
-   When testing, use the transport type that will be used in production. Unfortunately, all too often, functional testing is performed only by using the file adapter when some other transport will be used in production. Adopting this approach is setting you and the overall project up for failure later on.  
  
-   Validate the payload of all messages that are sent out from the system. If the messages are XML, you should validate their schema and key fields in the message using XPath expressions.  
  
-   Validate any tracking data stored in BAM (if used); any other data that is left in external data repositories should be accounted for.  
  
-   Test the execution of all Business Rule Engine (BRE) policies and rules if your solution uses BRE.  
  
### Negative tests  
  
-   Ensure you test the handling of invalid messages through your system. You should verify that your chosen strategy (to reject them before they come into BizTalk Server, or to suspend them) has worked correctly.  
  
-   When testing the handling of invalid messages, ensure you test that any receive-side error handling orchestrations have been implemented to handle suspended messages.  
  
-   Ensure that your failure scenarios cover all exception blocks in your orchestrations.  Failing to test this adequately is a common problem.  
  
-   If you are using long-running transactions with compensation behavior, test these scenarios very carefully. This is another area where inadequate testing will incur serious consequences in a production environment.  
  
-   Ensure failures are logged correctly in the appropriate error logs.  
  
## Automation is key  
 To do all of this efficiently and effectively, invest the time up front to automate testing. Manual testing is time consuming, error prone, and expensive (in terms of time and cost). Every time you perform a manual test pass, you add another batch of tasks that have to be handled by project resources (people in the team). By automating this up front, you are able to get a return on the initial investment that is required to develop the tests every time they are run. Good functional tests should execute quickly and efficiently and be repeatable; each test should also be autonomous (It should be independent of any other; adopting this approach enables you to run multiple tests sequentially as a test suite.) The functional tests should always produce the same result. Poorly written functional tests or poorly written code will result in different tests results between test runs, leading to confusion and wasted time investigating the root cause of the failure.  
  
 It is important to minimize the development effort required to write each functional test. Usually the more expensive it is to produce something (in terms of development time), the fewer test cases you are likely to end up with. This means you will have a lower level of test coverage over your code. By using a test framework, you can develop test cases quicker and easier and, hence, make it easier to get full code coverage. Most good test frameworks use a declarative approach to defining tests. (That is, the configuration for a test is stored in a configuration file, which is typically an XML file.) Using a good test framework enables you to develop a full functional test suite in an agile and reliable manner and avoids having to “reinvent the wheel” over and over, so to speak.  
  
## MSBUILD support for BizTalk Server projects  
 BizTalk Server provides support for the Microsoft Build Engine (MSBUILD) platform, which accommodates the building of managed projects in build lab environments where Visual Studio is not installed. MSBUILD accommodates building projects from a command line and advanced functionality including MSBUILD logging and batching. For more information about MSBUILD, see [MSBuild Overview](http://go.microsoft.com/fwlink/?LinkId=131739) (http://go.microsoft.com/fwlink/?LinkId=131739).  
  
## See Also  
 [Implementing Automated Testing](../technical-guides/implementing-automated-testing.md)