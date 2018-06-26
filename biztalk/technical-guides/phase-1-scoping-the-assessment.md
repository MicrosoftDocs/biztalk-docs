---
title: "Phase 1: Scoping the Assessment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 667c3669-7314-4562-84bc-fbb1be1f0314
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Phase 1: Scoping the Assessment
This topic describes the aspects of the scope phase of a BizTalk Server performance assessment.  
  
 A common mistake when engaging in a performance assessment is to underestimate the scope of the performance assessment. If sufficient resources and time are not allocated beforehand, then the team responsible for the performance assessment will be unable to complete all of the tasks required to build out and test a complex production-like environment. The team working on the performance assessment should choose their battles carefully. Most performance assessments are performed within a very limited timeframe and so the team should identify and focus on one or two, maybe three at most, key performance objectives. The application to be tested should be specifically developed to focus on the identified performance objectives and should factor out all other technology variables as much as possible. This topic describes the aspects of the scope phase of a BizTalk Server performance assessment.  
  
## Considerations before beginning the performance assessment  
 The following factors should be considered before any other work is done for a performance assessment. These factors will help decide the general direction of the scope phase and are a good starting point for a performance assessment.  
  
### Message load  
 It’s important to consider right from the outset how you are going to replicate the message load that will actually be going through the production system. For instance, if in production 20 percent of the messages will be <20KB in size, 50 percent will be <100KB in size and the remaining 30 percent could be up to 1 MB in size, it is important that this be replicated in the lab.  
  
### Develop a brief detail of the scenarios to be tested  
 After you have identified the test cases that will be tested, it is important to identify the major components that are involved in them. This includes both BizTalk Server components (such as messaging and orchestrations) and other components, including third-party technologies such as MQSeries or SAP. It is very important that you be aware of all of these from the outset as it will help you gauge the complexity of the lab and will enable you to plan for the technical skills required during the engagement.  
  
### Identify which adapters will be used  
 It is of vital importance the performance assessment lab use the actual adapters that will be used in the production environment. Failure to use the actual adapters used in production causes problems because the performance of different adapters varies significantly. For instance, the File adapter is one of the fastest BizTalk Server adapters but it lacks some of the features required of some systems; in particular the File adapter does not provide support for transactions. Transaction support provides the ability to read messages and write them to the MessageBox database, all within the context of an MSDTC transaction. Transaction support incurs overhead. Therefore, using the File adapter to simulate a production scenario that requires transaction support would not be a viable comparison. In this scenario, the performance results are essentially invalid because they are very unlikely to reflect the actual performance of the production system.  
  
### Estimate time required for the performance assessment  
 Use the following guidelines to estimate the time required for the performance assessment:  
  
- Allocate two weeks of preparation time for setting up the testing environment. One week will be used to build out the required infrastructure, software components, and apply software updates. The second week will be dedicated to setting up the specific environment that duplicates the BizTalk Server production environment.  
  
- Allocate an additional week for each test case that will be analyzed during the performance assessment.  
  
- Allocate a week at the end of the actual performance assessment to document the findings of the performance assessment.  
  
  So for a typical performance assessment with two test cases, the estimated time to complete the assessment would be:  
  
  (two weeks of preparation time) + (two weeks for the actual performance assessment) + (one week to document findings) = five weeks total.  
  
## Documenting the performance assessment  
 As part of scoping the performance assessment, the details of the assessment should be documented in an engagement summary. This document should clearly define goals and objectives, stakeholders, and milestones for the performance assessment. This document will serve as a roadmap for the performance assessment, help ensure all stakeholders agree on the engagement details and serve to ensure the performance assessment stays on track. This document should be updated throughout the performance assessment and include a summary of results upon the conclusion of the performance assessment.  
  
### Goals and objectives  
 **Carefully define throughput and latency goals** - What performance criteria are you trying to maximize? Typically one or more of the following performance measures are the focus of a BizTalk Server performance assessment.  
  
- **Throughput** – Typically measured as the number of messages per time unit that can be processed over a specified time interval. For example, a throughput goal might be defined as the ability to process 100 messages per second for a period of 3 hours.  
  
- **Latency** – Usually defined as percentage of all messages that can be processed end-to-end within a given time interval, for example:  
  
  -   95 percent of all messages should be processed end-to-end within two seconds.  
  
  -   100 percent of all messages should be processed end-to-end within four seconds.  
  
- **Peak loads**  
  
- **Time to complete a batch of**  *X*  
  
- **Floodgate recovery scenarios**  
  
- **High-level architecture including hardware and software**  
  
  Performance goals should be measured in terms of “achieve highest possible *X* given hardware and software constraints.” Determine how the goal will be measured in advance. For example, “Maximum Sustainable Throughput of *X* end-to-end as measured by the counter ’XLang/s\orchestrations completed / second’”.  
  
> [!NOTE]  
>  In the examples above, *X* is placeholder for the unit that is the focus of the performance assessment. *X* could represent orchestrations, messages, or other performance metrics that are relevant to the BizTalk solution.  
  
### Is the desired performance attainable?  
 When evaluating performance considerations, you should first determine if the available hardware resources will be sufficient for meeting your performance goals. In some cases, the desired performance is simply not possible without additional investment in hardware. There is no magic formula that can be used to determine what performance is or is not possible given a specific hardware configuration as many factors influence the performance of the solution, including the complexity of orchestrations, custom code that is used, number of times that messages are persisted to the MessageBox database, and limitations of external systems. The table below provides a summary of hardware used to achieve specific performance goals for certain scenarios.  
  
> [!NOTE]  
>  The information below is provided for guidance only. The requirements of different BizTalk Server solution vary greatly so the values in this table should be used as a rough “rule of thumb” when estimating required hardware resources.  
  
### Sample hardware scenarios  
  
|Type of Processing|BizTalk Server computers|SQL Server computers|Throughput attained|Notes|  
|------------------------|------------------------------|--------------------------|-------------------------|-----------|  
|Orchestration exposed as a Web service, MQSeries adapter|-   6 BizTalk Server 2010 computers<br />-   Each server running two 3-GHZ dual core processors<br />-   Windows Server 2008 R2, 8GB memory|-   3 SQL Server 2008 R2 computers<br />-   Each server running four 3-GHZ dual core processors<br />-   64-bit, 16 GB memory<br />-   Single MessageBox database|95 orchestrations per second|-   Average latency 1.11s<br />-   99% messages processed with <2 seconds latency|  
|Messaging|6 BizTalk Server 2010 computers|3 SQL Server 2008 R2 computers|Peak throughput attained over a 2 hour period was 277 messages per second|Before optimizing solution, peak throughput was 125 messages per second|  
|Low-latency scenario using orchestrations and Web services|One dual processor BizTalk Server 2010 computer|One quad processor SQL Server 2008 R2 computer|60 orchestrations per second|< 350 millisecond latency achieved|  
|Low-latency scenario using orchestrations|23 Quad processor BizTalk Server 2010 computers|-   3 SQL Server 2008 R2 computers<br />-   One 16-CPU master MessageBox database<br />-   Two 8-CPU secondary MessageBox database computers|1156 orchestrations per second|As of January 2010 was the highest sustainable performance of BizTalk Server running orchestrations recorded|  
  
 After the available hardware infrastructure is deemed sufficient to achieve the desired performance, consider the following when scoping a BizTalk Server performance assessment:  
  
-   Which adapters and/or accelerators are required?  
  
-   What are the requirements for implementing orchestrations in the solution?  
  
-   Document throughput requirements: What are the maximum sustainable throughput requirements for the solution?  
  
-   Latency requirements: How responsive does the solution need to be for solicit-response and request-response scenarios?  
  
-   How well does the solution recover from periods of peak document load?  
  
-   What are the high availability requirements of the solution?  
  
-   What are the document tracking requirements of the solution?  
  
-   What are the performance characteristics of any dependent applications such as a remote Web service or other system? If dependent applications do not keep up with the required load, the overall system performance will be degraded accordingly.  
  
### Hardware information to consider during scope phase  
 When scoping the solution, create a high-level hardware diagram that includes the following:  
  
-   Computer architecture (such as x86, x64, and IA64)  
  
-   CPU requirements (such as type, speed, number, cores, and use of hyperthreading)  
  
-   RAM requirements for each computer  
  
-   Local disk storage (type, size, speed)  
  
-   SAN (storage requirements: number of LUNS; SAN card type)  
  
-   Network cards (number in each computer, 100 megabits per second (Mbps) versus 1 gigabit per second (1 Gbps).)  
  
-   How will firewalls be deployed in the solution?  
  
-   Will Network Load Balancing hardware be used?  
  
-   Are specific computers to be clustered?  
  
### Software information to consider during the scope phase  
 Equally important as the hardware information is the software stack that will be used during the performance assessment.  You should ensure you document the following information:  
  
-   Operating system for each computer ( 32 or 64 bit, clustered or not).  
  
-   Server software to be installed on each computer.  
  
-   Virtualization software used.  
  
-   Specific software features not typically installed such as COM+ rollup fixes or SQL Server host fixes that are required.  
  
### Determine if code changes are within the scope of the performance assessment  
 This is one of the most important things to determine during the scoping process.  BizTalk Server and the underlying components it uses (SQL Server, Windows, IIS and many more) can be optimized using the tuning techniques and configuration changes discussed in this guide. However, if an application has not been developed for optimal performance, it can hamper these performance gains. Therefore, code changes should only be removed from the scope if you have confidence a thorough code review has been completed before the application enters the lab. If necessary, you may agree that only certain changes be allowed, for example, the removal of persistence points within orchestrations.  
  
## Roles and responsibilities  
 One of the most important areas of running a performance assessment is to ensure the roles and responsibilities are clearly assigned. The following key roles should be assigned at the onset of the performance assessment:  
  
- **Engagement lead** - The engagement lead is responsible for owning the overall engagement end-to-end.  This role will typically be performed by a Senior Consultant or Architect.  Ideally this person should have experience in tuning BizTalk Server based systems.  Knowledge of SQL Server and any other technologies including third party ones is desirable.  Please note it is not necessary that the lead is an expert in all areas, but they need to have at least a working knowledge of the technology in order that they can work with the specialists in those areas and understand the optimizations that they are applying.  
  
- **Test designer** - It is necessary to have someone who is dedicated to designing and implementing the tests that will be executed during the lab.  This will involve deciding on the test framework that will be used to create tests, testing each of the tests to ensure that it will fulfill the requirements of the lab and ensuring that those responsible for running the tests are aware of how to use the client.  
  
- **Environment owner** - Having a representative environment within the lab that accurately reflects the production BizTalk Server environment is critical.  The person performing this role will be responsible for checking each item of the software and hardware stack used and validating that there are no significant differences. For example SQL Server 2008 R2 when running on the 32-bit platform can only address 4GB of physical memory without using either Physical Address Extensions (PAE) or Address Windowing Extensions (AWE). In SQL Server 2008 R2, 64-bit up to 1 terabyte of memory can be addressed (this is the current maximum physical memory supported by Windows Server 2008 R2). Therefore a significant difference between the customer and the lab environment would be the architecture of CPU used by BizTalk Server and SQL Server. In addition to these obvious factors, other less obvious factors, such as service pack levels and hotfixes installed, can impact performance of the environment.  
  
- **Build environment lead** - After a detailed specification has been drawn up for the performance assessment, someone should be assigned the responsibility of building the environment. This will include the hardware and software stack. In many cases one individual will be responsible for this (this is often the environment owner). However in a large enterprise the environment owner may need to be the liaison between different teams, who may each be responsible for various components of the solution. For example, one team may be responsible for the Windows build, another for SQL Server, and yet another team for BizTalk Server.  
  
- **Deployment lead** - It is necessary to have someone responsible for ensuring that the application is deployed correctly to BizTalk Server, that the correct bindings are configured and that any custom configuration is applied. This role will require a thorough knowledge of the solution and will require the knowledge to package an application and deploy an application and then validate that it is in a functioning state within the lab environment.  
  
- **Product specialists** – It is important to identify what product specialists are required for the performance assessment. The exact skills required depend upon the design and purpose of the BizTalk Server application.  
  
   One of the most common product specialist skills required is extensive knowledge of performance tuning SQL Server. These skills are required for two purposes: first, it is often necessary to perform SQL Server optimizations to optimize performance of the BizTalk databases and second, many BizTalk solutions make use of custom databases. The use of custom databases can become a bottleneck in the solution if the correct optimizations are not applied to the SQL Server environment. In order to identify and apply the appropriate database optimizations, the following SQL Server skills are typically required:  
  
  - Thorough understanding of SQL Server stored procedure code, including the ability to optimize existing stored procedures.  
  
  - Ability to identify and build missing database indexes.  
  
  - Ability to write scripts to split databases into multiple files.  
  
    > [!NOTE]  
    >  For more information on applying this optimization, see [Optimizing Filegroups for the Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md).  
  
  - Ability to identify performance problems using SQL Server 2008 R2 Performance Dashboard Reports.  
  
    > [!NOTE]  
    >  SQL Server 2008 R2 Performance Dashboard Reports is available for download at [http://go.microsoft.com/fwlink/?LinkId=118673](http://go.microsoft.com/fwlink/?LinkId=118673).  
  
    For each specialist technology involved in the performance assessment, a list of requirements should be defined as is done above for SQL Server. This ensures the resource obtained has clear expectations of what will be required of them. Another technology that frequently requires specialized knowledge during the performance assessment is IBM Websphere MQ. The list below illustrates the requirements specification for an IBM WebSphere MQ product specialist:  
  
  - Experience in the monitoring, maintenance, and customization of MQSeries.  
  
  - Experience with installation and migration of new versions of MQSeries.  
  
  - Ability to analyze and tune MQSeries performance.  
  
  - Perform MQSeries problem analysis.  
  
  - Knowledge of the processes and procedures related to MQSeries security, administration, recovery and automation.  
  
- **Documentation lead** - Continuously updating the lab documentation end-to-end throughout the performance assessment is vitally important. The overall successfulness of a lab engagement should not be judged until the optimizations have successfully been applied in the production environment and the system has obtained the desired level of performance. In order to do this, it is essential that a detailed record of the following information is kept:  
  
  -   High-level results summary of the lab  
  
  -   Unresolved issues  
  
  -   Resolved issues  
  
  -   Timeline for the lab  
  
  -   Lab progress  
  
  -   Implemented optimizations by category  
  
  -   Implemented optimizations in chronological order (to ensure that they can be applied in the same order in the production system)  
  
  -   High-level architectural diagram  
  
  -   Detail of the scenarios to be tested  
  
  -   Third party technologies involved  
  
  -   Lab hardware diagram  
  
  -   Contact list  
  
  -   Detailed hardware inventory  
  
  -   Appendix with full detailed results  
  
- **Developer** - Whether a developer is required depends very much on the scope of the engagement. If the code base has been locked down and the lab is there to test infrastructure and platform optimizations only then the services of a developer should not be required. This type of scenario can occur when performance testing is performed just before the “go-live” date of the production server. By this time, the code should have been locked down and full regression testing should be complete or in progress. Any changes to the code introduced in the lab could introduce a regression and, therefore, introduce risk to the production system. If code changes are permitted, then typically a developer will be required. The list below represents the skills typically required by a developer that is engaged in a BizTalk Server performance assessment:  
  
  -   Ability to identify and fix performance issues with orchestrations  
  
  -   Ability to identify and fix performance issues with pipelines  
  
  -   Familiarity with .NET including:  
  
      -   Enterprise library  
  
      -   Visual Studio F1 profiler expertise  
  
      -   Microsoft Visual Studio 2010 Ultimate or Visual Studio Test Professional 2010  
  
- **Test lead** - Ensuring an accurate, complete and thorough set of results is obtained is critical. The test lead is responsible for ensuring the required information is captured, analyzed appropriately, and distributed appropriately after every test run. It is important to consider how to capture the data, typically the test data is suitable for presentation using an Excel spreadsheet. The following list illustrates the data that should be captured for each test that is run during the lab:  
  
  - Test run number  
  
  - Date  
  
  - Total messages processed  
  
  - Messages processed per second  
  
  - Time started  
  
  - Time stopped  
  
  - Test duration in minutes  
  
  - Suspended messages / Total messages processed – This can be captured either from the BizTalk Administration console or by measuring the BizTalk Server performance counters using Performance Monitor.  
  
  - \# of messages that have failed processing  
  
  - \# or message that have been successfully processed  
  
  - Test client responses  
  
  - Client process duration average, measured in seconds - Typically this value is measured when implementing a synchronous messaging solution with BizTalk Server, in this case it is important to know the value for average client duration as this is typically representative of how long an end user is waiting for a response from the solution.  
  
  - Client process duration maximum value, measured in seconds  
  
  - Client process duration minimum value, measured in seconds  
  
  - BizTalk Server request/response latency, measured in seconds  
  
  - Orchestrations completed per second  
  
  - % of messages processed on time  
  
  - Value of **TestResultsLocation** variable used by Visual Studio Team System testing tools.  
  
  - Value of **TestResultsLocation** variable used by BizUnit.  
  
  - Any comments or recommendations  
  
    As well as collecting the results, the test lead should ensure that they monitor each test run to see if there are any trends. Performance improvements should be communicated to the rest of the team and should indicate how much performance was improved and which optimization was applied to achieve the improvement. At the end of day it is important that the test lead provides a summary of the tests that have been performed in the lab. This allows the stakeholders to be kept informed of the continued progress of the lab. The table below illustrates how this information might be put together in a sample update e-mail:  
  
  ### Test results summary  
  
  |Status|Throughput|Average Latency|%< 2 seconds|# of Test runs|# of BizTalk Server Computers|# of Messages|Average Message Size|Duration|  
  |------------|----------------|---------------------|-------------------|---------------------|------------------------------------|--------------------|--------------------------|--------------|  
  |Scale out|140 messages/second|0.777 seconds|99.3%|2|6|270,000|609 bytes|30 minutes|  
  |Best|50 messages/second|1.12 seconds|99.12%|17|2|360,000|609 bytes|2 hours|  
  |Baseline|30 messages/second|1.52 seconds|92.9 %|4|2|36,000|609 bytes|20 minutes|  
  |Goals|5 messages/second|< 2 seconds|90%|-|2|-|-|-|  
  
## Define all deliverables that are required at the onset of the performance assessment  
 It is important to agree upon deliverables that must be in place before embarking on a BizTalk Server performance assessment. The section below describes the deliverables that should be in place at the onset of the performance assessment.  
  
- **Application to be tested** – The complete application that will be used during the performance assessment must be available. It is important that the application is in a fully functioning state before beginning the performance assessment, otherwise there is risk of losing valuable lab testing time.  
  
- **Planning for automated build and deployment** - Before engaging in the performance assessment, an automated build and deployment process should be developed for the BizTalk Server solution to be tested. Automating the build process for an application enables you to do a continuous daily build process, which can then be accompanied by a set of build validation tests (BVTs) which test the functional flows through the system. This enables you to detect compilation and functional problems quicker and easier throughout the development lifecycle. Within the lab, this means that if any code changes are required you can quickly verify that the updated solution works without problems. Manually building, deploying and configuring an application for a performance lab can be a tedious and error prone task. Therefore it is recommended that an automation technique be used to accomplish the following build and deployment activities:  
  
  -   Get latest code from source control.  
  
  -   Build the complete solution.  
  
  -   Deploy the solution to the environment.  
  
  -   Create BizTalk applications.  
  
  -   Add BizTalk Server resources such as .dll files and bindings to BizTalk applications.  
  
  -   Import binding file to create ports and bind to orchestrations.  
  
  -   Export BizTalk applications as a Microsoft® Windows® Installer package so that it can be deployed in the testing or production environment.  
  
  > [!NOTE]  
  >  For more information about implementing an automated build process, see[Automating the Build Process](../technical-guides/automating-the-build-process.md)  
  
   MSBuild was introduced with the .NET framework 2.0 to enable developers to automate tasks such as those described earlier. Several BizTalk Server–specific MSBuild tasks are included with the SDC Tasks library, which is available for download from  [http://go.microsoft.com/fwlink/?LinkId=119288](http://go.microsoft.com/fwlink/?LinkId=119288).  
  
- **Test data to be used during the performance assessment** – The test data that is used has a considerable influence on the overall effectiveness and success of a performance assessment.  Consider the scenario where a BizTalk Server application utilizes messaging, orchestration and the Rules Engine. The Rules Engine is called from within a pipeline component on the receive side to determine which orchestration will be used to process the message; and it is also called from within the orchestration at various points to determine flow. The Rules Engine implements caching so that rules policy execution is optimized. Therefore, if a single message is used as test data during the performance assessment, test results may be skewed (due to caching) and you may obtain results that can’t be replicated in production.  
  
   Ideally the test data used during the performance assessment should be actual production data or a subset of production data. The test data should also simulate the load and pattern of traffic that will be flowing through the production system. Consider the following factors when defining requirements for test data:  
  
  - **Number of messages that will be flowing through the system in a given period** - This is normally expressed as messages per second or messages per hour.  
  
  - **Types of messages** – Are the messages flat file, XML, or binary?  
  
  - **Distribution of messages** – What percentage will be flat file, what percentage of each XML message type will be used?  
  
  - **Peak load processing requirements** - In many scenarios a large interchange may be processed during non-peak hours. For example a large batch of payments may be posted to a bank’s systems at midnight. If this is the case, ensure you are able to replicate this during testing.  
  
  - **Endpoints used to receive/send messages** - In many environments separate receive locations are configured to receive different types of messages. For example flat file messages may be received using the File adapter or the MQSeries adapter may be used to receive XML messages. While messages may all be processed by the same orchestration(s) they will have different entry points into the system. Each of these different receive locations can be hosted in a separate host; in fact doing this will often improve the overall performance of the system.  
  
    The table below provides an example of the information that should be captured when determining test data specifications:  
  
  ### Sample test data specification  
  
  |                                             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
  |---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  |           **Messages per second**           |                                                                                                                                                                                                                                                                                   -   Maximum throughput is key in this scenario<br />-   Goal of 50 messages per second<br />-   Low-latency is not a goal                                                                                                                                                                                                                                                                                    |
  |            **Type of messages**             |                                                                                                                                                                                                                                                                  -   Small XML messages, approximately 25 KB that conform to XML schema *X*<br />-   Medium XML messages, approximately 512 KB that conform to XML schema *Y*                                                                                                                                                                                                                                                                  |
  |        **Distribution of messages**         |                                                                                                                                                                                                          -   58% 25 KB (small XML messages)<br />-   25% 512 KB (medium XML messages)<br />-   11% 3 MB (medium binary data – PDF) – non compressible<br />-   4% 7.5 MB (large binary data – PDF) – non compressible)<br />-   2% 20 MB (large binary data – PDF) – non compressible                                                                                                                                                                                                          |
  |    **Peak load processing requirements**    |                                                                                                                                                                                                                                  Large binary data (20MB) will represent approximately 2% of data (as specified above) the time at which this is processed is non-predictable. The system must be able to accommodate these large messages at any given time.                                                                                                                                                                                                                                  |
  | **Endpoints used to receive/send messages** | **Small XML messages (25 KB)**<br /><br /> -   Receive location: PaymentXMLDocIn<br />-   Host: ReceiveHost<br />-   Pipeline used: XMLReceive<br /><br /> **Medium XML messages (512 KB)**<br /><br /> -   Receive location: PaymentXMLDocIn<br />-   Host: ReceiveHost<br />-   Pipeline used: XMLReceive<br /><br /> **Medium binary data (3 MB) – PDF – non compressible**<br /><br /> -   Receive location: BinaryDataIn<br />-   Host: ReceiveHost<br />-   Pipeline used: PassThruReceive<br /><br /> **Large binary data (7.5 MB – 20 MB) – PDF – non compressible**<br /><br /> -   Receive location: BinaryDataIn<br />-   Host: ReceiveHost<br />-   Pipeline used: PassThruReceive |
  |          **Location of test data**          |                                                                                                                                                                                                                                                                                                    Locally accessible test data file share, for example: \\\PerformanceLabs\July\Test Data\                                                                                                                                                                                                                                                                                                    |
  
   Putting the information into a table accomplishes several things. First off, it makes it easier for stakeholders to agree on assumptions made about the test data. Second, it provides you with information that can be used to decide on potential optimizations for the performance assessment. For example in the table above you can see that all the receive locations used to process all different data types are hosted within the ReceiveHost BizTalk host. This means that each instance of this host will be responsible for processing different types and sizes of data (e.g. XML and binary non-compressible PDF data). Given that each host instance is a single instance of the BizTalk Server process (BTSNTSVC.EXE), this could become a processing bottleneck. Therefore in this scenario one immediately obvious optimization for the environment would be to test the performance improvement of separating each receive location into its own individual host. Having access to the test data information in a summary tabular format makes it easier to gauge simple optimizations such as this.  
  
- **Planning for automated load tests and load generation** - After the test data profile for the performance assessment is established, it is important to consider how to perform load testing within the environment. For BizTalk Server 2010 load test, we used Visual Studio 2010 load test. For more information about how to facilitate load testing using Visual Studio 2010, see [Using Visual Studio to Facilitate Automated Testing](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md).  
  
## See Also  
 [Phases of a Performance Assessment](../technical-guides/phases-of-a-performance-assessment.md)