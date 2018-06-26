---
title: "WCF Adapter FAQ: Development Libraries | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d05b635a-d46d-4f7d-896b-8ed7a799e80f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Adapter FAQ: Development Libraries
## When does it make more sense to use the WCF adapters vs. a WCF custom binding to communicate with an external application or system?  
 The BizTalk Server WCF adapters facilitate two new approaches to integrating an external system with BizTalk Server using WCF:  
  
- You can write WCF client/service code and use the standard BizTalk Server WCF adapters to handle the communication.  
  
- Alternatively you can develop a new custom WCF binding by using the .NET WCF framework and use it in place of the WCF adapter to handle the communication.  
  
  Using the WCF adapters with BizTalk Server, you can develop WCF client code and call BizTalk Server as a remote WCF service, or you can write a WCF service and configure BizTalk Server to expose it as a WCF service. The alternative is that you could actually write a whole new custom WCF binding to handle the communication.  
  
  The advantage of writing standard WCF client or service code and using the standard BizTalk Server adapters over writing a WCF custom binding element is that the custom binding is much harder to develop. The resulting WCF client or service exists outside of the BizTalk Server management (monitoring, configuration, and deployment) universe. The advantage of writing your own new custom binding and hosting it using a BizTalk WCF custom adapter is that it can be tightly integrated into these BizTalk Server management functions. The cost associated with developing a binding with respect to the infrastructure support is considerably more expensive than with developing a service.  
  
  It is important to understand that both approaches give you the opportunity to integrate with the internal BizTalk MessageBox database in a transactional manner and can offer similar performance. It’s more a decision of how complex you want to make the solution.  
  
  When using WCF you should first attempt to write a custom service and client and use the standard BizTalk WCF adapters to connect the two. The .NET Framework and WCF libraries are specifically geared toward making this task easy. To create the WCF service, simply develop your custom interface, set the appropriate attributes, and implement the code behind the contract. WCF takes care of everything from the metadata to the object serialization. Having written your WCF service you can then configure a WCF adapter through a send port to talk to the service in a few simple steps. You can even configure transactions so your new service can participate in a transactional exchange of messages with the internal BizTalk MessageBox database.  
  
  On the receive side you can configure BizTalk Server so that a receive location looks just like a WCF service on the network. That allows you to write regular WCF client code, and you can even use transactions when you call that service. The advantage of using a standard BizTalk WCF adapter as a configurable bridge directly from the WCF client to the WCF service code is that the development story is very simple. A WCF adapter provides a high-performance, transactional bridge into BizTalk Server from the WCF services environment in a simple fashion.  
  
  In summary, to communicate with an external system, you can write a WCF service to interact with an external system, and then write code to talk directly to the WCF service as a simpler solution to your problem. Using a more complex approach, you can write a new custom binding and integrate with BizTalk Server using one of the WCF custom adapters in a tighter fashion than by using the WCF service. Writing a new custom binding is lower-level and complex development exercise. The benefit of this approach is that you arrive at a tightly integrated solution where the BizTalk Server administration, configuration, and development story is being used uniformly across the whole solution. If the functionality of the adapter is developed as an external WCF client and service, then the configuration must be outside of the BizTalk Server environment and thus lacks the associated infrastructural support.  
  
## What are the differences between the WCF adapters and the adapters in the BizTalk Adapter Pack?  
 The WCF adapters are the seven adapters that come standard with the BizTalk Server release:  
  
- WCF-Custom  
  
- WCF-CustomIsolated  
  
- WCF-NetTcp  
  
- WCF-BasicHttp  
  
- WCF-WsHttp  
  
- WCF-NetNamedPipe  
  
- WCF-NetMsmq  
  
  The [BizTalk Adapter Pack](http://www.microsoft.com/biztalk/en/us/adapter-pack.aspx) is a post-BizTalk Server release that provides a single solution to easily and securely connect to Line-of-Business (LOB) data from any custom-developed .NET application, SQL Server-based business intelligence solution, or Office Business Application (OBA). The three adapters available in this release are Siebel, SAP, and Oracle DB. The Adapter Pack license is included with BizTalk Server Developer, Standard, and Enterprise editions, but is not included with the Branch edition. Customers that have already purchased BizTalk Server with Software Assurance will also have access to the BizTalk Adapter Pack through that program.  
  
## What is the recommended order for deciding to use the BizTalk Server Adapter Framework, the WCF LOB Adapter SDK, or the .NET Framework?  
 The BizTalk Adapter Framework is the least-preferred option because it is not based on standard .NET WCF. Because strategically your solution should include WCF most likely, what is the best way to do this? The easiest option is to write a WCF client and service, and then use a WCF adapter to tie them together. If the program is external to BizTalk Server, you can then write a WCF custom binding with the .NET Framework.  
  
 The only time you would choose the WCF LOB Adapter SDK as an option is if you are trying to solve a heavily metadata-centric LOB integration issue. The WCF LOB Adapter SDK is just another way to create a WCF binding, and it specializes in metadata support. An example of this metadata requirement is when the system you are communicating with does not have a fixed type of document. BizTalk Server sends or receives XML documents and the metadata describes the layout of the data in the document so the target system can use it.  
  
## What are the differences between the BizTalk Adapter Framework and the WCF LOB Adapter SDK?  
 The BizTalk Adapter Framework is used to build custom WCF adapters when none of the seven standard WCF adapters meets communication requirements. The Adapter Framework offers rich support for metadata to support LOB applications, and to share the standardized configuration and management methods used by the standard WCF adapters.  
  
 The WCF LOB Adapter SDK allows you to write a custom binding for a target system with heavy metadata requirements. The goal of the WCF LOB Adapter SDK is to facilitate uniform development of reusable metadata-oriented WCF-based adapters that enable enterprise applications and databases to integrate with each other. Because using the WCF LOB Adapter SDK produces a WCF binding, the same developed solution can be reused in multiple .NET applications including custom .NET applications, BizTalk Server, Microsoft Office SharePoint® Server, and Microsoft SQL Server Integration Services. In addition, the WCF LOB Adapter SDK provides a common metadata object model to expose target system metadata, for adapter consumers to browse, search, and retrieve WCF contracts from the adapter. You can download the SDK from [http://go.microsoft.com/fwlink/?LinkID=96184](http://go.microsoft.com/fwlink/?LinkID=96184).  
  
 While the BizTalk Adapter Framework and the WCF LOB Adapter SDK have similarities in that they help facilitate the development of custom adapters, there are some differences worth noting:  
  
- The WCF LOB Adapter SDK is a newer release and is based upon the .NET Framework 3.0 classes. Like the earlier BizTalk Adapter Framework it provides rich functionality in regards to metadata processing and managing connection; however, the resulting adapter is not tied to the BizTalk Server architecture.  
  
- An adapter written by using the WCF LOB Adapter SDK is exposed as a custom binding and is thus available to be called by any WCF client application. It can also be extended as a WCF channel. An adapter written by using the BizTalk Adapter Framework can be called only by BizTalk Server.  
  
  There is no explicit development tool support for the BizTalk Adapter Framework. For the WCF LOB Adapter SDK, the Adapter Code Generation Wizard takes you through a series of steps to gather various information that your custom adapter will need to use, and then generates files for you to use in your custom adapter project.