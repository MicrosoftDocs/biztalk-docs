---
title: "Types of Message Failures | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "transformation stage"
  - "assembly stage"
  - "errors, disassembly stage"
  - "errors, assembly stage"
  - "routing, errors"
  - "errors, transformation stage"
  - "errors, messages [HAT]"
  - "errors, routing"
  - "disassembly stage, errors"
  - "messages, errors [HAT]"
ms.assetid: 3a8e1c58-4b53-4439-837d-aaa233eb9158
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Types of Message Failures
This topic lists different points where a message failure may occur.  
  
 **Failures in the disassembly phase**  
  
 Processing might also fail during the disassembly phase; that is, failure in one of the pipeline components. For example, decryption failed due to absence of decryption cert on the processing server, or parsing failure due to problem either in the schema or in the message.  
  
 **Failures in routing**  
  
 After a message disassembles successfully, the next potential failure point is routing; for example, users enable a corresponding receive location of an orchestration and forget to enlist the orchestration. In this case, the message picked up from the receive location fails routing and the MessageBox database generates a Routing Failure report.  
  
 Routing Failure reports are listed in the BizTalk Server Administration Console as non-resumable suspended messages. Each Routing Failure report contains a message property snap shot taken when the routing failure occurred. You can use the information in each report to determine why routing failed for its associated message. If the associated message is resumable, you can correct the routing problem and resume the message so that processing continues. Routing Failure reports are listed in the results list with a blank service name and service type. When you terminate a suspended instance, the Routing Failure report associated with the suspended instance is automatically deleted by the Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb job that runs every minute by default. For more information about the Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb job, see [Database Structure and Jobs](../core/database-structure-and-jobs.md).  
  
 **Failures during the transformation phase**  
  
- **Received Messages**. When a message is received from Receive Location, the message is disassembled (for example, decrypted and parsed), the message might optionally be transformed to a different format via an Inbound Map specified on a receive Port, and published to the MessageBox for routing to an orchestration or a Send Port. In this case, processing may fail during transformation phase due to incorrect Inbound Map, or problems in the schema or in the message received.  
  
- **Sent Messages**. When a message is to be sent to a Send Location, an Outbound Map configured on Send Port might optionally transform the message. Then the transformed message is assembled and handed to the adapter for final transmission to the Send Location. In this case, processing may fail during transformation phase due to incorrect Outbound Map or problem in schema or source message.  
  
  **Failures in the message assembly phase**  
  
  Processing can also fail during message assembly phase – in other words, failing in pipeline component. After a message successfully assembles, the next potential failure point becomes transmission to Send Location; for example, the Send Location (which belongs to the partner) might be down or not exist.  
  
## See Also  
 [Investigating Orchestration, Port, and Message Failures](../core/investigating-orchestration-port-and-message-failures.md)