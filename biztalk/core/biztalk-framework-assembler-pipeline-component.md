---
title: "BizTalk Framework Assembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components, BizTalk Framework Assembler"
  - "BizTalk Framework Assembler [pipeline component]"
ms.assetid: 116dff8d-b7f8-4564-a7fb-6440682683dc
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Framework Assembler Pipeline Component
The BizTalk Framework is one approach for doing exactly-once guaranteed delivery using over-the-wire transport protocols such as HTTP or SMTP. This framework has existed since 1998, and can be thought of as a precursor to pending standards initiatives based on Web services, specifically WSReliable. Typically, the problem of guaranteed exactly-once delivery of data has been the domain of technologies like Message Queuing (also known as MSMQ). However, such technologies usually require common software at the two endpoints of a data flow, and also do nothing to address the use of open transport protocols based on public networks, for example, data that flows across enterprise boundaries by using the Internet.  
  
 Not surprisingly, the BizTalk Framework implements some of the same mechanisms present in earlier attempts to solve this problem of guaranteed exactly-once delivery of data. A good example of other solutions to the problem is electronic data interchange (EDI), where ANSI X12 control numbers and standard 997 functional acknowledgment documents form the basis of guaranteeing that data is received only one time, and that the sender is notified of any problems on the receiving end.  
  
 The BizTalk Framework assumes that, however disparate the systems trading data, they both understand the BizTalk Framework protocol requirements of:  
  
- Using a predictable envelope format for wrapping transmissions.  
  
- Tagging every outbound transmission with a globally unique identifier.  
  
- Always returning to the sender an acknowledgment of receipt that includes the globally unique identifier, even for data already received, acknowledged, and processed.  
  
- Some means by which the sender can repeat transmission until either a receipt arrives from the receiver, or some time period passes beyond which the transmission is no longer valid.  
  
  The BizTalk Framework Assembler pipeline component is responsible for serializing the BizTalk Framework envelope and contents onto the message before transmission and resending in the event that a receipt does not arrive in the allotted time period. It is also responsible for receiving and processing the receipts and deleting the message instance. (A copy of the message instance of the sent message is kept in the MessageBox database until BizTalk receives a confirmation receipt from the destination. After the confirmation receipt is received, the message instance is deleted by the Messaging Engine.)  
  
## See Also  
 [How to Configure the BizTalk Framework Assembler Pipeline Component](../core/how-to-configure-the-biztalk-framework-assembler-pipeline-component.md)   
 [Pipeline Components](../core/pipeline-components.md)