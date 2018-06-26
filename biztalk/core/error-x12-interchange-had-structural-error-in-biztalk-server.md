---
title: "The interchange had structural error. Last structurally valid functional group ID was: | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd62855b-ecc6-4cfd-be9c-0025348eb841
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The interchange had structural error. Last structurally valid functional group ID was:
## Details  
  
|                 |                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                 |
| Product Version |                                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                             |
|    Event ID     |                                                                         -                                                                          |
|  Event Source   |                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                               |
|    Component    |                                                                     EDI Engine                                                                     |
|  Symbolic Name  |                                                     X12InterchangeStructuralErrorAfter1stGroup                                                     |
|  Message Text   | The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error. Last structurally valid functional group ID was '{3}' |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange, because a structural error occurred in the interchange after the indicated functional group. This may have occurred with an interchange that was being preserved, with transaction sets suspended on the error. As a result of this error, the transaction set (or sets) that included the error was suspended, but the rest of the transaction sets were processed as part of the preserved batch.  
  
## User Action  
 To resolve this error, have the sender of the interchange fix the structural error, and then resend the interchange.