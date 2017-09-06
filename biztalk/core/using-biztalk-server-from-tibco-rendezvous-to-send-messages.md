---
title: "Using BizTalk Server from TIBCO Rendezvous to Send Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, sending"
  - "sending messages"
  - "BizTalk Server, using from TIBCO Rendezvous"
ms.assetid: 72057d42-32b5-4748-81e4-5ffb89630f5a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using BizTalk Server from TIBCO Rendezvous to Send Messages
Microsoft BizTalk Adapter for TIBCO Rendezvous uses the asynchronous API (Transport.Send). You can specify what kind of message the adapter sends using a message context property:  
  
-   **Structured**: The adapter generates a TIBRVMSG_MSG structured message, based on the XML data received from BizTalk Server. (*)  
  
 If BizTalk Server sends a message with fields that have names longer than 127 characters, BizTalk Adapter for TIBCO Rendezvous truncates the names to the maximum field name size for TIBCO Rendezvous, which is 127.  
  
 If a `reply subject name` property is provided, it is used to set the reply subject on the TIBCO Rendezvous message. It is assumed that either a receive port is set to listen for the reply and forward it to BizTalk Server, or some other TIBCO Rendezvous program is taking care of the reply.  
  
 The triplet (service, daemon, network) makes up the transport configuration. An empty (default) transport configuration results in a message being sent through the default transport object.  
  
 If the code page is left unspecified, the adapter uses UTF-8 encoding (code page 65001). Certified Messages are not supported on the transmitter side.  
  
## See Also  
 [TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md)   
 [Creating TIBCO Rendezvous Send Handlers](../core/creating-tibco-rendezvous-send-handlers.md)