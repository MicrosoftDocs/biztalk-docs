---
title: "HL7 Systems Integration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f66a4fc-186c-415f-a7ed-31f620f0495f
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Systems Integration with BizTalk Server
Microsoft BizTalk Server is an integration server designed for eBusiness applications. It is built on the  Windows Server, SQL Server, and SharePoint, and leverages the functionality of  Visual Studio. This technology stack provides a range of functionality and features for developing, implementing, operating, and maintaining your solution.  
  
 BizTalk Server provides the following integration services that you can use in conjunction with BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]).  
  
## Message Integration  
 BizTalk Server integrates different entities (departments, business partners, vendors, and so on) by automating message exchange. It uses Extensible Markup Language (XML) as a common communication protocol. It uses XML Schema Definition (XSD) schemas to describe and validate messages, and XSL Transformations (XSLT) to transform data from one message to another.  
  
 The BizTalk Server integration engine routes messages from one location to another. It features a publisher/subscriber model that enables one department to publish a document, and another to subscribe to it. The subscribing department can subscribe to the message without the publishing department knowing about it. This enables efficient handling of partner organizations, replacing point-to-point communications with a flexible hub-spoke arrangement.  
  
## Business Process Automation  
 BizTalk Server automates and integrates business processes by using a process map called an orchestration to link a set of distinct, related actions in a single process. By creating an orchestration, you can link steps based on data exchange and analysis, such as message receiving, message sending, decisions, loops, and other operations. An orchestration enables you to create a business process that will run automatically when an event occurs.  
  
 Using BizTalk Server, you can dynamically change a process based on business rules. This gives you the flexibility to change the actions taken in an orchestrated process according to business considerations. An example is restricting the approval process for billing orders to those orders over a certain threshold.  
  
 BizTalk Server also enables you to include human actions within automated orchestrations, through Human Workflow Services.  
  
## Integration of Heterogeneous Systems  
 BizTalk Server can integrate IT systems in a heterogeneous environment in which systems transmit data in different communications protocols. It does so by using adapters to connect to systems using different protocols. It supports the use of File, FTP, HTTP, SMTP, SOAP, and SQL adapters. You can create custom adapters by using the BizTalk Adapter Framework.  
  
## Role-based Tools  
 BizTalk Server is a development and execution environment in which developers, IT professionals, and business professionals collaborate to create, implement, operate, maintain, and customize the system. BizTalk Server provides each of these roles with tools tailored to their use.  
  
 For more information, see [A Role-based Product](../../adapters-and-accelerators/accelerator-hl7/a-role-based-product1.md).
  
## See Also  
 [What BizTalk Accelerator for HL7 Adds to BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/what-biztalk-accelerator-for-hl7-adds-to-biztalk-server.md)