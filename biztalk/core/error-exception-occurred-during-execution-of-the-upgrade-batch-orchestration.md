---
title: "An exception has occurred during the execution of the upgrade batch orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2221a498-98aa-43ab-bc4e-34dcbd92dcf0
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# An exception has occurred during the execution of the upgrade batch orchestration
## Details  
  
|                 |                                                                                                       |
|-----------------|-------------------------------------------------------------------------------------------------------|
|  Product Name   |          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]           |
| Product Version |                      [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                       |
|    Event ID     |                                                   -                                                   |
|  Event Source   |                                          BizTalk Server EDI                                           |
|    Component    |                                            Batching Engine                                            |
|  Symbolic Name  |                                     ExceptionOccuredDuringUpgrade                                     |
|  Message Text   | An exception has occurred during the execution of the upgrade batch Orchestration. ErrorMessage = {0} |
  
## Explanation  
 The Error/Warning/Information event indicates that the upgrade batch orchestration could not process the message correctly because of the error condition indicated in ErrorMessage field.  
  
## User Action  
 To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and then resubmit the message.