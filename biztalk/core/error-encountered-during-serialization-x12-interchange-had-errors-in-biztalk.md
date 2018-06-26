---
title: "Error encountered during serialization. The X12 interchange had the following errors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9ca3314-6c66-4400-816a-f9c7c7915122
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error encountered during serialization. The X12 interchange had the following errors
## Details  
  
|                 |                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                              |
| Product Version |                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                          |
|    Event ID     |                                                                      -                                                                      |
|  Event Source   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                            |
|    Component    |                                                                 EDI Engine                                                                  |
|  Symbolic Name  |                                                           X12InterchangeSendError                                                           |
|  Message Text   | Error encountered during serialization. The X12 interchange with id '{0}', with sender id '{1}', receiver id '{2}' had the following errors |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing X12 interchange because of the stated errors.  
  
## User Action  
 To resolve this error, use the information in the error message to identify the error in the interchange and then determine the problem resolution in the product help.