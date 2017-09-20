---
title: "Systems Integration with BizTalk Server1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "system integration"
  - "BizTalk Server, tools"
  - "business processes, automating"
  - "BTAHL7, BizTalk Server"
  - "BizTalk Server"
  - "BizTalk Server, business process automation"
  - "BizTalk Server, messages"
  - "BizTalk Server, system integration"
ms.assetid: 8f66a4fc-186c-415f-a7ed-31f620f0495f
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Systems Integration with BizTalk Server
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] is an integration server designed for eBusiness applications. It is built on the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsWinSvrNoVersion](../../includes/btswinsvrnoversion-md.md)] System platform, including [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Windows Server 2008, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)], and [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], and leverages the functionality of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[vs2012](../../includes/vs2012-md.md)]. This technology stack provides a range of functionality and features for developing, implementing, operating, and maintaining your solution.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides the following integration services that you can use in conjunction with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]). For more information about [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] integration services, see [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.  
  
## Message Integration  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] integrates different entities (departments, business partners, vendors, and so on) by automating message exchange. It uses Extensible Markup Language (XML) as a common communication protocol. It uses XML Schema Definition (XSD) schemas to describe and validate messages, and XSL Transformations (XSLT) to transform data from one message to another.  
  
 The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] integration engine routes messages from one location to another. It features a publisher/subscriber model that enables one department to publish a document, and another to subscribe to it. The subscribing department can subscribe to the message without the publishing department knowing about it. This enables efficient handling of partner organizations, replacing point-to-point communications with a flexible hub-spoke arrangement.  
  
## Business Process Automation  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] automates and integrates business processes by using a process map called an orchestration to link a set of distinct, related actions in a single process. By creating an orchestration, you can link steps based on data exchange and analysis, such as message receiving, message sending, decisions, loops, and other operations. An orchestration enables you to create a business process that will run automatically when an event occurs.  
  
 Using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can dynamically change a process based on business rules. This gives you the flexibility to change the actions taken in an orchestrated process according to business considerations. An example is restricting the approval process for billing orders to those orders over a certain threshold.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] also enables you to include human actions within automated orchestrations, through Human Workflow Services.  
  
## Integration of Heterogeneous Systems  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can integrate IT systems in a heterogeneous environment in which systems transmit data in different communications protocols. It does so by using adapters to connect to systems using different protocols. It supports the use of File, FTP, HTTP, SMTP, SOAP, and SQL adapters. You can create custom adapters by using the BizTalk Adapter Framework.  
  
## Role-based Tools  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is a development and execution environment in which developers, IT professionals, and business professionals collaborate to create, implement, operate, maintain, and customize the system. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides each of these roles with tools tailored to their use.  
  
 For more information, see [A Role-based Product](../../adapters-and-accelerators/accelerator-hl7/a-role-based-product1.md), and [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.  
  
## See Also  
 [What BizTalk Accelerator for HL7 Adds to BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/what-biztalk-accelerator-for-hl7-adds-to-biztalk-server.md)