---
title: "Error encountered during parsing. The X12 transaction set contained in functional group is being suspended with following errors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51c6fa8e-d81c-4ccb-93b4-852ab184c4e9
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error encountered during parsing. The X12 transaction set contained in functional group is being suspended with following errors
## Details  
  
|                 |                                                                                                                                                                                                                                      |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                          |
| Product Version |                                                                                      [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                      |
|    Event ID     |                                                                                                                  -                                                                                                                   |
|  Event Source   |                                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                                        |
|    Component    |                                                                                                              EDI Engine                                                                                                              |
|  Symbolic Name  |                                                                                                    X12TransactionSetReceiveError                                                                                                     |
|  Message Text   | Error encountered during parsing. The X12 transaction set with id '{0}' contained in functional group with id '{1}', in interchange with id '{2}', with sender id '{3}', receiver id '{4}' is being suspended with following errors: |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming X12 interchange because of the stated errors with the identified transaction set.  
  
## User Action  
 To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution in the product help.