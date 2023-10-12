---
description: "Learn more about: Error encountered during serialization. The Edifact transaction set contained in functional group is being suspended with following errors"
title: "Error encountered during serialization. The Edifact transaction set contained in functional group is being suspended with following errors"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Error encountered during serialization. The Edifact transaction set contained in functional group is being suspended with following errors
## Details  
  
| Field | Error Details |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                               |
| Product Version |                                                                                           [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                           |
|    Event ID     |                                                                                                                       -                                                                                                                        |
|  Event Source   |                                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                                             |
|    Component    |                                                                                                                   EDI Engine                                                                                                                   |
|  Symbolic Name  |                                                                                                          EfactTransactionSetSendError                                                                                                          |
|  Message Text   | Error encountered during serialization. The Edifact transaction set with id '{0}' contained in functional group with id '{1}', in interchange with id '{2}', with sender id '{3}', receiver id '{4}' is being suspended with following errors: |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing EDIFACT interchange because of the stated errors with the identified transaction set.  
  
## User Action  
 To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution in the product help.
