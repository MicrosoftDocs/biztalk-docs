---
title: "MQSeries Adapter Message Flow | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MQSeries adapters, message flow"
ms.assetid: aa5c8523-afd6-4181-9c11-a150857a7790
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MQSeries Adapter Message Flow
A message originating from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer is first passed to an MQSeries Server running on Windows. MQSeries Server running on Windows can be on the same computer as the one that runs BizTalk Server. The message is routed through the MQSeries Server for Windows computer to an MQSeries Server host on an operating system such as UNIX. An application then retrieves the message from the MQSeries queue.  

 A message originating from an application first goes to an MQSeries queue on MQSeries Server. The MQSeries Server forwards the message to the MQSeries Server for Windows computer. BizTalk Server receives the message from the MQSeries Server for Windows computer and forwards it to the appropriate application.  

 The MQSeries adapter supports the following messaging scenarios.  


|        **Scenario**        |                                                                                                                                                                                                                 **Description**                                                                                                                                                                                                                 |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          Receive           |                                                                                                                                           The adapter receives a message from MQSeries Server, which is passed to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].                                                                                                                                           |
| Send (Static One-Way Port) |                                                                                                                                                      The adapter routes a message that originates from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].                                                                                                                                                      |
|        Dynamic Send        |                                                                                                                                                                                   Enables the application to select a destination address (URI) at run time.                                                                                                                                                                                    |
|      Dynamic Receive       |                                                                                                                             Enables the application to select a source address (URI) at run time by setting the **MQSeries.DynamicReceive** context property to **Yes** and specifying the dynamic receive address.                                                                                                                             |
|        Correlation         | Messages from the adapter are correlated with specific instances of an orchestration that can handle more than one type of message.<br /><br /> MQSeries Server can create the correlation identifier by using solicit-response, or BizTalk Server can create the correlation identifier.<br /><br /> For more information about correlation sets, see [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help. |

 For more information about using ports and adapters in pipelines, orchestrations, and content-based routing, see [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help. For more information about using correlation identifiers in the adapter, see [Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md).  

 For information about the header properties available for filtering in the adapter, see [Properties Related to BizTalk Server](../core/properties-related-to-biztalk-server.md) and [MQSeries Context Properties](../core/mqseries-context-properties.md).  

## See Also  
 [Using the MQSeries Adapter](../core/using-the-mqseries-adapter.md)