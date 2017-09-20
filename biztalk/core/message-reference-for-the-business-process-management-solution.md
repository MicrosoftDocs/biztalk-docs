---
title: "Message Reference for the Business Process Management Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "process management solution tutorial, message reference"
ms.assetid: 0595817e-da5d-426a-9ee1-0c5d04334de6
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Reference for the Business Process Management Solution
This section lists the messages and message types used by each orchestration in the solution.  
  
 In the table, \<*SolutionPrefix*> replaces Microsoft.Samples.BizTalk.SouthridgeVideo to make the table easier to read.  
  
> [!NOTE]
>  A message type of **System.Xml.XmlDocument** indicates a message type defined by a .NET class rather than a schema.  
  
 The orchestrations, messages, and types are as follows.  
  
|Orchestration|Message|Message Type|  
|-------------------|-------------|------------------|  
|Activate.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|Activate.odx|OrderMsg|\<SolutionPrefix>.Schemas.OrderSchema|  
|Analyze.odx|BadXmlOrderMsg|System.Xml.XmlDocument|  
|Analyze.odx|FixedXmlOrderMsg|System.Xml.XmlDocument|  
|Analyze.odx|OrderMsg|\<SolutionPrefix>.Schemas.OrderSchema|  
|Analyze.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|CableOrder1.odx|TerminatedMsg|\<SolutionPrefix>.SchemaClasses.Terminated|  
|CableOrder1.odx|OrderMgrMsg|\<SolutionPrefix>.OrderManager.OrderMgrMsgType|  
|CableOrder1.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|CableOrder1.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|CableOrder1.odx|CompletionMsg|\<SolutionPrefix>.OrderManager.OrderMgrMsgType|  
|CableOrder1.odx|OrderMsg|\<SolutionPrefix>.Schemas.OrderSchema|  
|CableOrder1.odx|AckMsg|\<SolutionPrefix>.SchemaClasses.OrderAck|  
|CableOrder1.odx|InterruptMsg|\<SolutionPrefix>.SchemaClasses.Interrupt|  
|CableOrder2.odx|OrderMgrMsg|\<SolutionPrefix>.OrderManager.OrderMgrMsgType|  
|CableOrder2.odx|TerminatedMsg|\<SolutionPrefix>.SchemaClasses.Terminated|  
|CableOrder2.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|CableOrder2.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|CableOrder2.odx|OrderMsg|\<SolutionPrefix>.Schemas.OrderSchema|  
|CableOrder2.odx|CompleteOrderMsg|\<SolutionPrefix>.Schemas.OrderSchema|  
|CableOrder2.odx|AckMsg|\<SolutionPrefix>.SchemaClasses.OrderAck|  
|CableOrder2.odx|CompletionMsg|\<SolutionPrefix>.OrderManager.OrderMgrMsgType|  
|Cancel.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|Cancel.odx|OrderMsg|\<SolutionPrefix>.Schemas.OrderSchema|  
|Cancel.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|Change.odx|OrderMsg|\<SolutionPrefix>.Schemas.OrderSchema|  
|CheckInterrupt.odx|InterruptMsg|\<SolutionPrefix>.SchemaClasses.Interrupt|  
|Complete.odx|OrderMsg|\<SolutionPrefix>.Schemas.OrderSchema|  
|Complete.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|ErrorHandler.odx|InterruptMsg|\<SolutionPrefix>.SchemaClasses.Interrupt|  
|ErrorHandler.odx|OrderStatusMsg|\<SolutionPrefix>.SchemaClasses.OrderStatus|  
|ErrorHandler.odx|ResponseMsg|\<SolutionPrefix>.SchemaClasses.OrderStatus|  
|ErrorHandler.odx|OriginalMsg|System.Xml.XmlDocument|  
|ErrorHandler.odx|ReturnedMsg|System.Xml.XmlDocument|  
|ExceptionHandler.odx|OriginalMsg|System.Xml.XmlDocument|  
|Interrupter.odx|InterruptMsg|\<SolutionPrefix>.SchemaClasses.Interrupt|  
|OrderBroker.odx|CSRConfMsg|\<SolutionPrefix>.OrderBrokerSchemas.CSR_OrderRequestSchema|  
|OrderBroker.odx|CSROrderMsg|\<SolutionPrefix>.OrderBrokerSchemas.CSR_OrderRequestSchema|  
|OrderBroker.odx|HistoryInsertMsg|\<SolutionPrefix>.OrderBrokerSchemas.SQLHistoryInsertSchema.HistoryInsert|  
|OrderBroker.odx|ServicingMsg|\<SolutionPrefix>.OrderBrokerSchemas.Servicing_OrderRequestSchema|  
|OrderBroker.odx|OrderMsg|\<SolutionPrefix>.Schemas.OrderSchema|  
|OrderBroker.odx|OrderMgrMsg|\<SolutionPrefix>.OrderBroker.OrderMgrMPMsg|  
|OrderManager.odx|CompletionMsg|\<SolutionPrefix>.SchemaClasses.OrderStatus|  
|OrderManager.odx|NewOrderMgrMsg|\<SolutionPrefix>.OrderManager.OrderMgrMsgType|  
|OrderManager.odx|OrderMgrMsg|\<SolutionPrefix>.OrderManager.OrderMgrMsgType|  
|OrderManager.odx|OrderAck|\<SolutionPrefix>.SchemaClasses.OrderAck|  
|OrderManager.odx|TerminatedMsg|\<SolutionPrefix>.SchemaClasses.Terminated|  
|OrderManager.odx|ErrorMsg|\<SolutionPrefix>.OrderManager.OrderMgrMsgType|  
|Validate.odx|BadXmlOrderMsg|System.Xml.XmlDocument|  
|Validate.odx|FixedXmlOrderMsg|System.Xml.XmlDocument|  
|Validate.odx|OrderMsg|\<SolutionPrefix>.Schemas.OrderSchema|  
  
## See Also  
 [Business Process Management Solution Reference](../core/business-process-management-solution-reference.md)   
 [Key Messages and Fields](../core/key-messages-and-fields.md)   
 [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md)