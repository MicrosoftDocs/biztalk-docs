---
title: "BizTalk Server Message Context Properties (Send Handlers) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a065ba89-9fdb-47dc-9021-fb95cf347cdc
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Server Message Context Properties (Send Handlers)
In addition to the message payload, the supplementary information that a message contains must be accessible from the BizTalk Server orchestration at run time.  
  
## TIBCO RV Message Information Promoted as Message Context Properties  
  
|Data Identification|Type|Routable|Send Location|  
|-------------------------|----------|--------------|-------------------|  
|Send Subject|string|Yes|Orchestration specifies the TIBCO Rendezvous send subject. Default value is Null. Mandatory unless a default subject is specified in the port configuration.|  
|Reply Subject|string|Yes|Orchestration provides a subject for reply messages, when pertinent. Default value is Null.|  
  
## Getting a TIBCO Reply  
 **Question:** How does BizTalk Adapter for TIBCO Rendezvous read and manipulate the reply subject inside an orchestration so that you can use it as the send subject for the response? How does the adapter get to the message context of an incoming message from Rendezvous?  
  
 **Answer:** The reply subject is populated in the context of the incoming message, and the orchestration can read it. If the orchestration ultimately produces a reply, it can use that value to set the send subject of the reply message.  
  
1. In a BizTalk Server project, add a reference to <install_directory>\TibcoRV\bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll.  
  
2. In the orchestration (somewhere between the Receive shape that is handed the incoming Rendezvous message and the Send shape that is sending the reply), add a message construction/assignment shape (or an expression shape) to do something like the following example to the reply you constructed:  
  
   ```  
   OutgoingMsg(Rendezvous.SendSubject) = IncomingMsg  
   (Rendezvous.ReplySubject);  
   ```  
   ## Management assembly
   TIBCO Rendezvous does not provide metadata repositories, and Microsoft BizTalk Adapter for TIBCO Rendezvous management assembly does not provide browsing capabilities or schema generation. Therefore, you must provide a schema to BizTalk Server. For more information, see [Install, schemas, & limitations](../core/installing-biztalk-adapter-for-tibco-rendezvous.md).
  
   BizTalk Adapter for TIBCO Rendezvous includes a schema with predefined types. The adapter uses these types when generating messages for some specific data types (arrays).

  
## See Also  
 [Data Type Mapping for Send Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md)   
 [Creating TIBCO Rendezvous Send Handlers](../core/creating-tibco-rendezvous-send-handlers.md)