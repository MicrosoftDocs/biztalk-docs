---
title: "An exception has occurred during the batch submission in the batching orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c58b2fa9-d036-4e09-a0f8-77a2f983881a
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# An exception has occurred during the batch submission in the batching orchestration
## Details  
  
|                 |                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                  |
| Product Version |                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                              |
|    Event ID     |                                                          -                                                          |
|  Event Source   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                |
|    Component    |                                                   Batching Engine                                                   |
|  Symbolic Name  |                                                  ExceptionOccured                                                   |
|  Message Text   | An exception has occured during the batch submission in the batching Orchestration. Batch Id= {0}, ErrorMessage {1} |
  
## Explanation  
 This Error/Warning/Information event indicates that the batching orchestration could not add a batch element to a batch because of the error condition indicated in the ErrorMessage field.  
  
## User Action  
 To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and then resubmit the message.