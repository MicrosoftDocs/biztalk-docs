---
title: "The interchange had structural error. The part after the error is being suspended | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9071825d-7b90-42bf-bcf9-2a15ae36086d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The interchange had structural error. The part after the error is being suspended
## Details  
  
|                 |                                                                                                                                                                                |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                               |
| Product Version |                                                           [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                           |
|    Event ID     |                                                                                       -                                                                                        |
|  Event Source   |                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                             |
|    Component    |                                                                                   EDI Engine                                                                                   |
|  Symbolic Name  |                                                                        EfactInterchangeStructuralError                                                                         |
|  Message Text   | The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error. The part after the error is being suspended, refer to Suspended Queue for details |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming EDIFACT interchange, because a structural error occurred in the interchange. This occurred with an interchange that was being preserved, with transaction sets suspended on the error. As a result of this error, the transaction set (or sets) that included the error was suspended, but the rest of the transaction sets were processed as part of the preserved batch.  
  
## User Action  
 To resolve this error, have the sender of the interchange fix the structural error, and then resend the interchange.