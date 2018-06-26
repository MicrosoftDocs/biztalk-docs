---
title: Edifact transaction set contained in interchange error | Microsoft Docs
description: Error encountered during serialization. The Edifact transaction set contained in interchange (without group) is being suspended with following errors
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a0a33ac-d83e-495c-ba75-88c15ad7cfcd
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Edifact transaction set is suspended error and details

`Error encountered during serialization. The Edifact transaction set contained in interchange (without group) is being suspended with following errors`

## Details  
  
|                 |                                                                                                                                                                                                                              |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                      |
| Product Version |                                                                                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                  |
|    Event ID     |                                                                                                              -                                                                                                               |
|  Event Source   |                                                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                                    |
|    Component    |                                                                                                          EDI Engine                                                                                                          |
|  Symbolic Name  |                                                                                           EfactTransactionSetSendErrorWithoutGroup                                                                                           |
|  Message Text   | Error encountered during serialization. The Edifact transaction set with id '{0}' contained in interchange (without group)  with id '{1}', with sender id '{2}', receiver id '{3}' is being suspended with following errors: |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing EDIFACT interchange because of the stated errors with the identified transaction set. Note that the transaction set is not in a group in the interchange.  
  
## User Action  
 To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution.