---
title: "BizTalk Server Message Context Properties (Receive Handlers) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message context properties"
  - "receive handlers, message context properties"
ms.assetid: 7f47e2a0-6ac8-404a-bc0a-c7739911af74
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Server Message Context Properties (Receive Handlers)
In addition to the message payload, the supplementary information that composes a message must be accessible from a BizTalk Server orchestration at run time.  
  
## TIBCO RV Message Information Promoted as Message Context Properties  
 The following table lists this supplementary information:  
  
|Data Identification|Type|Routable|Receive Location|  
|-------------------------|----------|--------------|----------------------|  
|Send Subject [null]|string|Yes|Tells orchestration which subject this message was sent to.|  
|Reply Subject [null]|string|Yes|Tells orchestration where the sender expects the reply to be sent, if one is expected.|  
|Field Count [read only]|unsigned int|No|Number of fields in upper level message. A property provided by TIBCO RV.|  
|CM Sender Name [read-only]|string|Yes|CM Correspondent name of the sender.|  
|CM Sequence Number [read only]|long|No|Sequence number assigned by the sending TIBCO transport object.|  
|CM Time Limit [read-only]|double|No|A time limit, after which the sending program no longer expects its CM transport to certify delivery of the message.|  
  
## See Also  
 [Message Mapping in TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md)   
 [Creating TIBCO Rendezvous Receive Handlers](../core/creating-tibco-rendezvous-receive-handlers.md)