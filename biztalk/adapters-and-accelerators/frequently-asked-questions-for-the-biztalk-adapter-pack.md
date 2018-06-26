---
title: "Frequently asked questions for the BizTalk Adapter Pack | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0cdaf09a-50fe-4f30-bd9d-60e316351846
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Frequently Asked Questions
Frequently asked questions (FAQs) about the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  


## General questions

### What are the supported BizTalk versions for the BizTalk Adapter Pack?  
 The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] is included with Microsoft [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. Install the version included with your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version. Installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] from another [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version is not supported. 

### In which user context should the setup be run?  
Run the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] setup using an account that is a member of the local administrators group and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. 

Related link: [Minimum Security Rights](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)

### How do I get started using the adapter?  
If you're familiar with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] and the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], then install [BAP 2016](../adapters-and-accelerators/install-the-biztalk-adapter-pack-2016.md) or [BAP 2013 R2 and 2013](../adapters-and-accelerators/install-biztalk-adapter-pack-2013-r2-and-2013.md), and then get started with the the [different adapters](../adapters-and-accelerators/biztalk-adapter-pack.md).

If you're brand new [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] or the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], then look at the get started topics, and step through the tutorials: 

[Get started with the BizTalk Adapter for Oracle Database](../adapters-and-accelerators/adapter-oracle-database/get-started-with-the-oracle-database-adapter.md)  
[Get started with the BizTalk Adapter for Oracle E-Business Suite](../adapters-and-accelerators/adapter-oracle-ebs/get-started-with-the-biztalk-adapter-for-oracle-e-business-suite.md)  
[Get started with the BizTalk Adapter for mySAP Business Suite](../adapters-and-accelerators/adapter-sap/get-started-with-the-biztalk-adapter-for-mysap-business-suite.md)  
[Get started with the BizTalk Adapter for Siebel eBusiness Applications](../adapters-and-accelerators/adapter-siebel/get-started-with-the-biztalk-adapter-for-siebel-ebusiness-applications.md)  
[Get started with the BizTalk adapter for SQL](../adapters-and-accelerators/adapter-sql/get-started-with-the-biztalk-adapter-for-sql.md)

### Does the Microsoft BizTalk Adapter Pack support tracing?  
The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] enables adapter clients to enable Windows Communication Foundation (WCF) tracing and adapter-specific tracing. When you enable tracing, you also choose the folder path and file name. So, the traces are stored where you prefer. To view the traces, use the WCF Service Trace Viewer tool. See [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](https://msdn.microsoft.com/library/aa751795.aspx).

For more information about tracing, and other troubleshooting ideas, see: 

[Troubleshoot the Oracle Database adapter](../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)  
[Troubleshoot the Oracle EBS adapter](../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)  
[Troubleshoot the SAP adapter](../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)  
[Troubleshoot the Siebel adapter](../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)  
[Troubleshoot the SQL adapter](../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)  

### Are performance counters available for the adapters?  
Yes. The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] provides a **LOB Time (Cumulative)** performance counter to measure the time, in milliseconds, that the LOB client library takes to complete an action initiated by the adapter.  You can enable the performance counters by setting the `EnablePerformanceCounters` binding property to **True**. To disable performance counters, set `EnablePerformanceCounters` to **False** (the default value).   

## BizTalk Server questions

### Which BizTalk Server tools are used while working with adapters? Where can I find more information about these tools?  
There are several tools that can help with the artifacts that use these adapters: 


|                                  Tool                                  |                                                                                                                                                                                           Topics in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] core documentation                                                                                                                                                                                            |
|------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] | -   [Using Visual Studio](../core/using-visual-studio.md) <br />-   [Working with BizTalk Projects](../core/working-with-biztalk-projects.md)<br />-   [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)<br /><br /> Learn more about Visual Studio solutions, projects, and items at [Solutions and Projects in Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx). |
|                         Orchestration Designer                         |                                                                                                                                                                                       [Creating orchestrations using orchestration designer](../core/creating-orchestrations-using-orchestration-designer.md)                                                                                                                                                                                        |
|                           Pipeline Designer                            |                                                                                                                                                                                                 [Creating pipelines using pipeline designer](../core/creating-pipelines-using-pipeline-designer.md)                                                                                                                                                                                                  |
|                             BizTalk Mapper                             |                                                                                                                                                                                                         [Creating maps using BizTalk mapper](../core/creating-maps-using-biztalk-mapper.md)                                                                                                                                                                                                          |
|                 BizTalk Server Administration console                  |                                                                                                                                                                                            [Using the BizTalk Server Administration console](../core/using-the-biztalk-server-administration-console.md)                                                                                                                                                                                             |

### Can I reuse bindings of a BizTalk application? How?  
Yes. A binding creates a mapping between a logical endpoint, such as an orchestration port or a role link, and a physical endpoint, such as a send and receive port. This enables communication between different components of a BizTalk business solution. The binding information is stored in an XML file that contains binding information for each BizTalk orchestration in the scope of a BizTalk assembly, application, or group. You can export the bindings of a BizTalk assembly, application, or group, and then reuse it by importing into any other BizTalk application or group. For more information, see 

[Reuse Oracle DB adapter bindings](../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)  
[Reuse Oracle EBS adapter bindings](../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)  
[Reuse SAP adapter bindings](../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)  
[Reuse Siebel adapter bindings](../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md)  
[Reuse SQL adapter bindings](../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)

### What is the “Transaction Isolation Level”? How can I configure it?  
 The transaction isolation level determines the degree to which a transaction is isolated from the data changes made by other transactions. It defines the locking behavior of the Transact-SQL commands issued by a connection to the Line-of-Business (LOB) system. 

This is configurable for some of the adapters. See: 

[Oracle Database: Configure transaction isolation level and transaction timeout](../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)  
[Oracle E-Business Suite: Configure transaction isolation level and transaction timeout](../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)  
[SQL: Configure Transaction Isolation Level and Transaction Timeout](../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)

[Isolation Levels in the SQL Database Engine](https://technet.microsoft.com/library/ms189122.aspx) describes the different levels in SQL. 

## WCF-based adapter FAQs

### What is WCF?
 WCF stands for Windows Communication Foundation. WCF is a programming framework developed by Microsoft for building service-oriented applications. WCF is a part of .NET framework, and enables developers to build secure, reliable, and transacted solutions that integrate across platforms and interoperate with existing investments.  

Related link: [What Is Windows Communication Foundation](https://msdn.microsoft.com/library/ms731082.aspx)  

### What is WCF LOB Adapter SDK?  
 The WCF LOB Adapter SDK is a collection of tools and components that provide a consistent framework for developing reusable, metadata-rich adapters for line-of-business systems. Adapters written using the WCF LOB Adapter SDK are surfaced as custom WCF bindings and can be consumed by a WCF-capable client. 

Related link: [WCF Line of Business Adapter SDK documentation](../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md) 

### What is the WCF service model?  
 The WCF service model is a programming model provided by WCF in which the LOB system (such as Oracle or SAP) is exposed as a WCF service. The service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface. The WCF service model generates a proxy class — the WCF client class — through which your code can invoke operations and receive data using the adapter. 

 All adapters in the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] support the WCF service model.

 ### What is the WCF channel model?  
 The WCF channel model is a low-level abstraction of the SOAP message exchange between clients and services. It provides interfaces and types that enable you to send and receive messages by using a layered protocol stack called a channel stack. Each layer of the stack is composed of a channel, and each channel is created from a WCF binding. Each adapter is a WCF custom transport binding that exposes the LOB system as a WCF service. 

  All adapters in the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] support the WCF channel model.

### When should I use the WCF service model or the WCF channel model?  
 The WCF service model presents a model that is familiar to .NET programmers, and hides the underlying complexities of SOAP message exchange over a channel. Moreover, the Add Adapter Service Reference Plug-in is integrated with the Visual Studio design experience, and presents a standard Microsoft Windows interface that provides powerful browsing and searching capabilities on operations exposed by the adapter. Therefore, the WCF service model is often the best choice to develop programming solutions for any WCF-based adapter.  

 You want to use the WCF channel model over the WCF service model when:  

-   The WCF channel model provides more fine-grained control over the operations that you perform on the LOB system because in the WCF channel model, you directly control the contents of the messages that you send over the channel.  

-   The WCF channel model provided more comprehensive support for end-to-end streaming of large object (LOB) data types than the WCF service model. This is because in the WCF channel model, you directly control how you provide the message body on outgoing messages and how you process the message body on incoming messages. 

### How do I get started with the WCF service model?  
 You can use either of the following tools provided by the WCF service model to generate a WCF client class or a WCF service contract and associated helper code from the service metadata exposed by each adapter:  

- The ServiceModel Metadata Utility Tool (svcutil.exe), which ships with WCF.  

- The Add Adapter Service Reference Visual Studio Plug-in, which ships with the [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)].  

### How do I get started with the WCF channel model?  
 Using the WCF channel model, you can invoke operations and receive the results of a polling query by exchanging SOAP messages with the adapter over a WCF channel. To get started, you need to create outbound (client) and inbound (service) channels.

## See Also  
[BizTalk Adapter Pack](../adapters-and-accelerators/biztalk-adapter-pack.md)