---
title: "An exception has occurred during the execution of the routing orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68ec8921-ba05-496e-8dcc-fd8994fcb8b7
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# An exception has occurred during the execution of the routing orchestration
## Details  
  
|                 |                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------|
|  Product Name   |       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]       |
| Product Version |                   [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                   |
|    Event ID     |                                               -                                                |
|  Event Source   |     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI     |
|    Component    |                                        Batching Engine                                         |
|  Symbolic Name  |                                 ExceptionOccuredDuringRouting                                  |
|  Message Text   | An exception has occured during the execution of the routing Orchestration. ErrorMessage = {0} |
  
## Explanation  
 This Error/Warning/Information event indicates that the routing orchestration could not process each copy of the XML batch element correctly because of the error condition indicated in ErrorMessage field.  
  
## User Action  
 To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and resubmit the message.