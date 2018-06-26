---
title: "WCF Run-Time Errors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5591bd4-aa15-4c7a-903e-fc73b880692f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Run-Time Errors
Information for diagnosing and resolving WCF run-time events.  
  
## WCF service host restarted
  
|                 |                                   Error details                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                       0x1FB0                                       |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                          BTS_I_WCF_SERVICE_HOST_RESTARTED                          |
|  Message Text   |                                         0                                          |
  
## Explanation  
 This message provides a way for the WCF adapter to write an “informational” event log entry (the provided APIs for adapters allow the creation of warnings or errors, not information).  
  
## User Action  
 If you see this informational event in the event log, it indicates that the auto-recovery has succeeded. No further action in regard to this message is necessary.