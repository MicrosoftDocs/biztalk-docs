---
title: "About Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations"
  - "Orchestration Designer"
  - "orchestrations, about orchestrations"
  - "Orchestration Designer, about Orchestration Designer"
ms.assetid: c0d9a3fb-da87-42cc-9e9e-e2c37232e606
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# About Orchestrations
An orchestration is a flexible, powerful tool for representing an executable business process based on XLANG/s language. XLANG/s can be viewed as a messaging language with some of the expression capabilities of C#. You can design flow, interpret and generate data, call custom code, and organize the entire process in an intuitive visual drawing, and at run time, the BizTalk Orchestration Engine executes XLANG/s files which are the executable business processes that are produced by BizTalk Orchestration Designer.  
  
 Messages, the send and receive actions that operate on them, and the ports through which they are transported are all fundamental elements of an orchestration. The message is the medium by which orchestrations communicate with the outside world and by which e-business is conducted.  
  
 **Receive** and **Send** shapes encapsulate the functionality you need to receive messages into your orchestration and send messages from it. You should become familiar with the various shapes that Orchestration Designer provides to represent the logical flow of your orchestration.  
  
 You should understand advanced orchestration concepts such as Web services, correlation, and long-running transactions. You might not need to use all of these facilities, but it is helpful to know what they can do for you.  
  
 Web services are programs with interfaces that adhere to the standards set forth in the Web Services Description Language (WSDL). By defining message types, ports, port types, and operations in a standard way, disparate systems can communicate effectively with each other.  
  
 Correlation is the mechanism by which messages are associated with particular running instances of an orchestration, so that your business process gets the appropriate information when many instances are running and many messages are being sent back and forth.  
  
 Transactions enable you to maintain the state of an orchestration appropriately if any unexpected issues arise. Orchestration Designer provides various ways to handle exceptions, which enable you to deal with errors in a controlled and predictable manner.  
  
## In This Section  
  
-   [The Orchestration Design Surface](../core/the-orchestration-design-surface.md)  
  
-   [BizTalk Orchestrations Tab, Toolbox](../core/biztalk-orchestrations-tab-toolbox.md)  
  
-   [Steps in Orchestration Development](../core/steps-in-orchestration-development.md)  
  
-   [Security Considerations for Developing Orchestrations](../core/security-considerations-for-developing-orchestrations.md)  
  
-   [XLANG-s Language](../core/xlang-s-language.md)  
  
-   [About the BizTalk Orchestration Engine](../core/about-the-biztalk-orchestration-engine.md)