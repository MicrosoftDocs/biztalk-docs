---
title: "Error encountered during parsing. The Edifact transaction set contained in interchange (without group) is being suspended with following errors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 901fef68-4649-480a-997c-b061d7d069d6
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error encountered during parsing. The Edifact transaction set contained in interchange (without group) is being suspended with following errors
## Details  
  
|                 |                                                                                                                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                   |
| Product Version |                                                                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                               |
|    Event ID     |                                                                                                           -                                                                                                           |
|  Event Source   |                                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                                 |
|    Component    |                                                                                                      EDI Engine                                                                                                       |
|  Symbolic Name  |                                                                                      EfactTransactionSetReceiveErrorWithoutGroup                                                                                      |
|  Message Text   | Error encountered during parsing. The Edifact transaction set with id '{0}' contained in interchange (without group) with id '{1}', with sender id '{2}', receiver id '{3}' is being suspended with following errors: |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming EDIFACT interchange without a group because of the stated errors with the identified transaction set in the interchange. Note that the transaction set is not in a group in the interchange.  
  
## User Action  
 To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution in the product help.