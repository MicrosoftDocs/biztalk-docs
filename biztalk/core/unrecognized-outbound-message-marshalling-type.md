---
title: "Unrecognized outbound message marshalling type | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e675112b-12f3-47ff-95f7-ce1a05db120e
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Unrecognized outbound message marshalling type
## Details  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]               |
|    Event ID     |                                           0                                            |
|  Event Source   |                                           0                                            |
|    Component    |                                           0                                            |
|  Symbolic Name  |                                           0                                            |
|  Message Text   | Unrecognized outbound message marshalling type; expected UseBodyElement or UseTemplate |
  
## Explanation  
 The WCF.OutboundBodyLocation property is set to a value different than UseBodyElement or UseTemplate, in a custom pipeline component or orchestration.  
  
## User Action  
 Set the WCF.OutboundBodyLocation property to a valid value. Valid values are "UseBodyElement" or "UseTemplate" This is a code change.   
For further information about outbound messaging, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)  
  
-   [Configuring the WCF Adapters](../core/configuring-the-wcf-adapters.md)