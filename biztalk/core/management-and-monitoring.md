---
title: "Management and Monitoring | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92724f79-32bb-40d3-a0af-147aba00d87e
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Management and Monitoring
Every application built on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine requires management. How are new applications installed? What configurations are possible? What’s happening inside the system right now? This section looks at the tools provided to answer these questions.  
  
## Installing BizTalk Server  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes a number of components, and it depends on multiple aspects of the Windows environment. Making sure that the correct version of everything the product needs is available, then installing all of the product components correctly could potentially be a challenging process.  
  
 Installation is, however, straightforward. Upgrading from BizTalk Server 2009 is automatic, and all items built for this earlier version—orchestrations, maps, and so on—will continue to work. To ensure that the right environment exists, an administrator doing a new installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can download a standard .CAB file or reference an already available .CAB file that was downloaded earlier. In either case, this file contains the redistributable components that the product requires for installation. These include things such as the correct versions of Microsoft Data Access Components (MDAC), Microsoft XML Parser (MSXML), the latest security hot fixes, and other necessary software.  
  
 After the contents of this .CAB file have been installed, there are two main options for installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] itself. The default approach, typical of what developers creating a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment for their own use might do, installs all of the product’s components under a single account on one machine. After the process is started, the developer can just watch while these components are installed. An administrator setting up a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, by contrast, can use the custom configuration option. This choice allows deploying the product to different machines, defining and using different accounts, and other more detailed configurations.  
  
## Creating Scalable Configurations  
 If  high availability or redundancy are not requirements, the entire [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine can be installed on a single machine. In some situations, however, this would not be the right solution. Perhaps the number of messages the engine must handle is too great for one machine, or maybe redundancy is required to make the system more reliable. To meet requirements like these, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine can be deployed in a number of ways.  
  
 A fundamental concept for deploying the engine is the idea of a host. A host can contain various things, including orchestrations, adapters, and pipelines. Hosts are just logical constructs, however. To use them, a BizTalk Server administrator must create host instances.. Each host instance is a Windows process, and as the diagram below shows, it can contain various things. In the example shown here, Machine A is home to two host instances. One contains a receive adapter and receive pipeline, while the other contains the orchestrations P and Q. Machine B runs just one host instance, also containing the two orchestrations P and Q. Machine C, like machine A, is home to two host instances, but neither of them contains an orchestration. Instead, each of these instances contains a different send pipeline and send adapter. Finally, machine D houses the MessageBox database that is used by all of the host instances in this configuration.  
  
 ![](../core/media/understandingbts-09-hosts.gif "UnderstandingBTS_09_Hosts")  
  
 This example illustrates several ways in which hosts might be used. For instance, since both machines A and B are home to the orchestrations P and Q, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can automatically load balance requests to these orchestrations based on the availability and current load on each machine. This allows a BizTalk application to scale up as needed for high-volume processes. Notice also that machine C contains two different ways to handle outgoing messages. Perhaps one relies on a standard [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapter, such as the HTTP adapter, while the other uses a custom adapter to communicate with a particular system. Grouping all output processing on a single machine like this can make good sense in some situations. And because each host instance is isolated from every other host instance—they’re different processes—it is safer to run code that is not completely trusted, such as a new custom adapter, in a separate instance. It’s Even though this example contains only a single instance of the MessageBox database, it is possible to replicate or cluster it to avoid creating a single point of failure.  
  
 The abstraction of BizTalk applications introduced in the current version of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] isn’t intrinsically associated with hosts. For a simple BizTalk application, all of its components might be contained in a single host, with all of them installed on the same machine. In a more complex case, however, the various artifacts that make up the application—orchestrations, adapters, pipelines, and more—might be spread across multiple hosts on multiple machines, as in the figure above. Accordingly, the process of mapping these artifacts to physical machines doesn’t depend on the notion of a BizTalk application.  
  
## Managing Applications  
 The main tool for managing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine is the BizTalk Server Administration console, a Microsoft Management Console (MMC) snap-in that provides a user interface for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrators. While this tool gives administrators a number of capabilities, the most important are the ability to do three things:  
  
- **Deploy BizTalk applications.** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables administrators to work with a complete BizTalk application as a unit. Using the BizTalk Server Administration console, an administrator can create a BizTalk application, and deploy it to one or more servers.  
  
- **Configure BizTalk applications.** When developers create orchestrations, they works largely in logical terms. To define how the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine will communicate with a particular application, for example, the developer can select an HTTP adapter without worrying about the specific URL that will be used. Similarly, the developer can specify that the send pipeline should include a component that adds a digital signature to outgoing messages without worrying about exactly what key will be used to create this signature. Yet to make the application work, these details must be specified. The BizTalk Server Administration console allows an administrator to create and modify configurations like these.  
  
- **Monitor BizTalk applications.** Using the **Group Hub** page on the BizTalk Server Administration console, an administrator can monitor the operation of BizTalk applications. Group Hub shows information about the current status of these applications and they applications can be examined in various ways. Rather than requiring an administrator to search for problems, for example, the **Group Hub** page uses color-coded indicators to display those problems. This lets administrators take a more proactive approach to application monitoring.  
  
  The BizTalk Administration console, which relies on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]’s Management database, also provides other services. An administrator can dynamically add machines and specify what hosts should be assigned to them while an application is running. There’s no need to shut down the application to make these changes. The Administration console’s functions can also be accessed programmatically through Windows Management Instrumentation (WMI), which allows administrators to create scripts that automate management functions.  
  
## Reporting On and Debugging Applications  
 BizTalk applications do lots of things: send and receive messages, process those messages within orchestrations, communicate with various systems using different protocols, and more. Keeping a record of application activity, especially when failures occur, is very useful. Similarly, having some way to debug orchestrations and other application components is essential. Both of these features are provided by the Group Hub in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   The Group Hub provides graphical access to information about applications running on the engine. This information can include when an orchestration starts and ends, when each shape within it is executed, when each of its messages is sent and received, the contents of those messages, and more. A developer or administrator can even set breakpoints, allowing the orchestration to be stopped and examined at predetermined places. The Group Hub can also be used to examine archived data, looking for patterns and trends in the execution of a business process. This information is useful for debugging, answering business questions (such as verifying that a message really was sent to a customer), and keeping ongoing statistics that can be used to improve performance.  
  
## See Also  
 [The BizTalk Server Messaging Engine](../core/the-biztalk-server-messaging-engine.md)   
Install [BizTalk Server 2016](../install-and-config-guides/biztalk-server-2016-what-s-new-and-installation.md) or [BizTalk Server 2013 or R2](../install-and-config-guides/biztalk-server-2013-and-2013-r2-what-s-new-install-and-upgrade.md)    
[Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)  
 [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md)   
 [Using the Group Hub Page](../core/using-the-group-hub-page.md)