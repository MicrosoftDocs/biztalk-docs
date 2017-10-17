---
title: "Adapters in BizTalk Server | Microsoft Docs"
description: Complete list of all available adapters in BizTalk Server, including built-in adapters, enterprise adapters, and the BizTalk Adapter Pack
ms.custom: ""
ms.date: "10/16/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fd279fb-2c68-4de4-a586-5a8e42a685ff
caps.latest.revision: 48
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adapters in BizTalk Server
One of the primary design goals of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is to facilitate the exchange of business documents between trading partners. To help meet this goal, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes several adapters that provide connectivity between BizTalk Server and trading partners using commonly recognized data protocols and document formats. This topic discusses what an adapter is and why you use an adapter.  
  
## What Is an Adapter?  
 An adapter is a software component that enables you to easily send messages out of or receive messages into BizTalk Server with a delivery mechanism that conforms to a commonly recognized standard, such as SMTP, POP3, FTP, or Microsoft Message Queuing (MSMQ). As Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has evolved, the need for adapters that quickly enable connectivity with commonly used applications and technologies has increased.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes the following adapters, which are referred to as the "native" or "integrated" adapters: FILE, FTP, HTTP, MQSeries, MSMQ, POP3, SMTP, SOAP, Windows Sharepoint Services, and the seven WCF adapters (WCF-WSHttp, WCF-BasicHttp, WCF-NetTcp, WCF-NetMsmq, WCF-NetNamedPipe, WCF-Custom, and WCF-CustomIsolated). Native adapters are installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. You can also create custom adapters for your specific solutions by using the BizTalk Adapter Framework.  
  
 Each of the native adapters is associated with a receive location designed to listen for messages from a certain transport at a certain address. After the message is received by the receive location, it is passed to the adapter. The adapter attaches the data stream to the message (typically in the body part of the message), adds any metadata pertaining to the endpoint that the data was received from, and then submits that message into the BizTalk Messaging Engine.  
  
 By default, when you run the BizTalk Configuration Wizard, the wizard installs the native adapters and creates an adapter handler with a default configuration for each one.  
  
 Using the BizTalk Server Administration console, you can modify the default configuration for the adapter handlers as well as add, remove, and modify send ports and receive locations for the adapters. For more information about these processes, see the appropriate topics in See Also.  
  
## Why Use an Adapter?  
 Using adapters greatly simplifies the transfer of messages into or out of BizTalk Server. If your existing infrastructure uses any of the transports for which there is a corresponding BizTalk adapter, then the process of sending messages to or receiving messages from BizTalk Server is as simple as configuring the appropriate adapter to send or receive messages with the corresponding transport mechanism.  
  
## Functionality support in built-in adapters  
 The following table lists the primary benefit of each native adapter and whether the adapter provides the following features:  
  
-   **Transaction support** : The ability to send and receive documents under the context of a distributed transaction coordinator (DTC) transaction. This functionality is required for maintaining ordered message delivery and to guarantee that documents are not duplicated or lost.  
  
-   **Two-way communication support (Request/Response or Solicit/Response)** : The ability to send a document and process a response message from the destination or to receive a document and send a response message to the source.  
  
-   **In-order receive support** : The ability to publish received documents to the BizTalk MessageBox database in the exact order that the documents were received.  
  
-   **SSO enabled** : The ability to use SSO authentication when sending or receiving documents with the adapter.  
  
-   **Hosting process** : The process in which the adapter executes. *BizTalk IP* executes within the BTSNTSvc.exe process, while *IIS OOP* run outside the BizTalk Server process in the Internet Information Server (IIS) process.  
  
|Adapter|Primary benefit|Transaction support|Two-way communication support|In-order receive support|SSO enabled|Hosting process|  
|---|---|---|---|---|---|---|  
|Custom|Supports your system.|Yes, requires custom code.|Yes, requires custom code.|Yes, requires custom code.|Yes, requires custom code.|BizTalk IP|  
|File|Easy to use.|No|No|No|No|BizTalk IP|  
|FTP|Is widely used for business-to-business communications.|No|No|No|Yes|BizTalk IP|  
|HTTP(s)|Is widely used for business-to-business communications.|No|Request/Response and Solicit/Response|No|Yes|IIS OOP|  
|MSMQ|Supports guaranteed once-only delivery of messages between BizTalk Server and Microsoft Message Queuing.|Yes|No|Yes|No|BizTalk IP|  
|Logic App| Receive from, and send to an Azure Logic App. For on-premises and cloud environments, use this adapter to access many Azure services | Yes | Depends on your workflow design| | |Receive: BizTalk IP<br/>Send: IIS OOP| 
|MQ Series|Supports guaranteed once-only delivery of messages between BizTalk Server and IBM WebSphere MQ for Windows platforms.|Yes|No|Yes|Yes|BizTalk IP|  
|POP3|Supports receiving documents through e-mail.|No|No|No|No|BizTalk IP|  
|SMTP|Supports sending documents through e-mail.|No|No|No|No|BizTalk IP|  
|SOAP|Supports the use of Web services.|No|Request/Response and Solicit/Response|No|Yes|IIS OOP|  
|Windows SharePoint Services|Enables the exchange of XML and binary messages between BizTalk Server and SharePoint document libraries.|No|No|No|No|BizTalk IP| 
|WCF-WSHttp|Supports WS-* standards over the HTTP transport.|Yes, transactions are supported on WsHTTP (only WS-Transactions)|Request/Response and Solicit/Response|No|Yes|IIS OOP|  
|WCF-BasicHttp|Communicates with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1 using HTTP or HTTPS.|No|Request/Response and Solicit/Response|No|Yes|IIS OOP|  
|WCF-NetTcp|Supports WS-* standards over the TCP transport.|Yes|Request/Response and Solicit/Response|No|Yes|BizTalk IP|  
|WCF-NetMsmq|Supports queuing by leveraging Microsoft Message Queuing (MSMQ) as a transport.|Yes|No|Yes|Yes|BizTalk IP|  
|WCF-NetNamedPipe|Provides a fast transport for cross-process communication on the same machine ( only for WCF apps).|Yes|Request/Response and Solicit/Response|No|Yes|BizTalk IP|  
|WCF-Custom|Enables the use of WCF extensibility features.|Yes|Yes|Yes, as long as the binding supports it.|Yes|BizTalk IP|  
|WCF-CustomIsolated|Enables the use of WCF extensibility features over the HTTP transport.|Yes|Yes|No|Yes|IIS OOP|  
  
## Enterprise adapters  
 Following is a list of the Line of Business (LOB) adapters provided by Microsoft.  
  
|Adapter|Description|Supported Versions|  
|---|---|---|  
|PeopleSoft Enterprise|Enables exchange of Component Interface (CI) messages between BizTalk Server and a PeopleSoft system.|[Supported Line-of-Business (LOB) and Enterprise systems](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|JD Edwards OneWorld XE|Enables exchange of Business Function messages between BizTalk Server and a JD Edwards OneWorld system.|[Supported Line-of-Business (LOB) and Enterprise systems](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|JD Edwards EnterpriseOne|Enables exchange of Business Function messages between BizTalk Server and a JD Edwards EnterpriseOne system.|[Supported Line-of-Business (LOB) and Enterprise systems](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|TIBCO Rendezvous|Enables exchange of XML and binary data format messages between BizTalk Server and TIBCO Rendezvous.|[Supported Line-of-Business (LOB) and Enterprise systems](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|TIBCO Enterprise Message Service|Enables exchange of XML and binary data format messages between BizTalk Server and a TIBCO EMS server providing a tightly integrated and reliable application infrastructure.|[Supported Line-of-Business (LOB) and Enterprise systems](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  

## BizTalk Adapter Pack  
 You can also use the adapters that are shipped with [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] to connect to various line-of-business systems. For more information about [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], see [BizTalk Adapter Pack](../adapters-and-accelerators/biztalk-adapter-pack.md).
  
## See Also  
 [Best Practices for Securing Adapters](../core/best-practices-for-securing-adapters.md)   
 [Creating and Deleting Adapter Handlers](../core/creating-and-deleting-adapter-handlers.md)   
 [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)