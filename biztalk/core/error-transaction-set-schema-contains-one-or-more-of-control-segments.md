---
title: "Transaction set schema contains one or more of control segments ISA, IEA, GS, GE | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7589d8f0-c727-47df-afbc-77b0f190f3e2
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transaction set schema contains one or more of control segments ISA, IEA, GS, GE
## Details  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                       SchemaCode114EOtherControlSegmentsPresent                        |
|  Message Text   |    Transaction set schema contains one or more of control segments ISA, IEA, GS, GE    |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming transaction set or the send pipeline could not process the outgoing transaction set because the document schema for the transaction set defined at least one ISA, IEA, GS, or GE segment.  
  
## User Action  
 To resolve this error, undeploy the document schema, remove the ISA, IEA, GS, or GE segment from the schema, and then redeploy the schema.