---
title: "Systems Integration with BizTalk Server2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "system integration"
  - "tools, BizTalk Server"
  - "BizTalk Server, tools"
  - "BizTalk Server, about BizTalk Server"
  - "BizTalk Server, business processes"
  - "messages, BizTalk Server"
  - "BizTalk Server, messages"
  - "BizTalk Server, system integration"
  - "business processes, BizTalk Server"
ms.assetid: 5ba3dda1-efdb-4a2b-bb3a-825d76696f15
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Systems Integration with BizTalk Server
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] is an integration server designed for eBusiness applications. It is built on the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsWinSvrNoVersion](../../includes/btswinsvrnoversion-md.md)] System platform, including [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsWinSvrNoVersion](../../includes/btswinsvrnoversion-md.md)]® 2008, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 2008 R2/2008 SP1, and [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] SharePoint® Services, and takes advantage of the functionality of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. This technology stack provides a range of functionality and features for developing, implementing, operating, and maintaining your solution.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides the following integration services that you can use in conjunction with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]. For more information about [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] integration services, see [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Help.  
  
## Message Integration  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] integrates different entities (departments, business partners, vendors) by automating message exchange. It uses XML as a common communication protocol. It uses XML Schema Definition (XSD) schemas to describe and validate messages, and XSL Transformations (XSLT) to transform data from one message to another.  
  
 The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] integration engine routes messages from one location to another. It features a publisher/subscriber model that enables one department to publish a document, and another to subscribe to it. The subscribing department can subscribe to the message without the publishing department knowing about it. This enables efficient handling of partner organizations, replacing point-to-point communications with a flexible hub-spoke arrangement.  
  
## Business Process Automation  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] automates and integrates business processes by using a process map referred to as an orchestration to link a set of distinct, related actions in a single process. By creating an orchestration, you can link steps based on data exchange and analysis, such as message receiving, message sending, decisions, loops, and other operations. With an orchestration, you can create a business process that will run automatically when an event occurs.  
  
 Using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can dynamically change a process based on business rules. This gives you the flexibility to change the actions taken in an orchestrated process according to business considerations. An example is restricting the approval process for billing orders to those orders over a certain threshold.  
  
 By using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can include human actions within automated orchestrations through Human Workflow Services. For more information, see "Human Workflow Services (HWS)" in [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Help.  
  
## Integration of Heterogeneous Systems  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can integrate IT systems in a heterogeneous environment in which systems transmit data in different communications protocols. It does so by using adapters to connect to systems using different protocols. It supports using File, FTP, HTTP, SMTP, SOAP, and SQL adapters. You can create custom adapters by using the BizTalk Adapter Framework. For more information, see "Developing Adapters Using the Adapter Framework" in [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Help.  
  
## Role-Based Tools  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is a development and execution environment in which developers, IT professionals, and business professionals collaborate to create, implement, operate, maintain, and customize the system. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides each of these roles with tools customized to their use.  
  
 For more information, see [A Role-Based Product &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/a-role-based-product2.md), and [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Help.  
  
## See Also  
 [How BizTalk Server Solves the Business Need](../../adapters-and-accelerators/accelerator-rosettanet/how-biztalk-server-solves-the-business-need1.md)   
 [What BizTalk Accelerator for RosettaNet Adds to BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)