---
title: "Error encountered during serialization. The Edifact interchange which did not contain a group had the following errors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af693139-e4cd-4bcb-922c-79caa148d3b7
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error encountered during serialization. The Edifact interchange which did not contain a group had the following errors
## Details  
  
|                 |                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                      |
| Product Version |                                                                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                  |
|    Event ID     |                                                                                              -                                                                                              |
|  Event Source   |                                                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                    |
|    Component    |                                                                                         EDI Engine                                                                                          |
|  Symbolic Name  |                                                                          EfactFunctionalGroupSendErrorWithoutGroup                                                                          |
|  Message Text   | Error encountered during serialization. The Edifact interchange which did not contain a group, with interchange id '{0}', with sender id '{1}', receiver id '{2}' had the following errors: |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing EDIFACT interchange because of the stated errors with the identified interchange. Note that the interchange does not contain a group.  
  
## User Action  
 To resolve this error, use the information in the error message to identify the error in the interchange and then determine the problem resolution in the product help.