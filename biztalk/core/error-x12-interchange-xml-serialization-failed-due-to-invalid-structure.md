---
title: "X12 interchange Xml serialization failed due to invalid structure. Looking for TransactionSet or GE, but not found | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d058fdbb-6be5-499f-86f7-0eb8a85c5fb2
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# X12 interchange Xml serialization failed due to invalid structure. Looking for TransactionSet or GE, but not found
## Details  
  
|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| Product Version |                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                             |
|    Event ID     |                                                         -                                                          |
|  Event Source   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI               |
|    Component    |                                                     EDI Engine                                                     |
|  Symbolic Name  |                                           X12TransactionSetOrGeNotFound                                            |
|  Message Text   | X12 interchange Xml serialization failed due to invalid structure. Looking for TransactionSet or GE, but not found |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not serialize the outgoing interchange because the structure of the interchange was invalid. The reason could be that the required headers or trailers are not present or are invalid. It could occur if a transaction set in a group is not followed by another transaction set or the group trailer. It could also occur if structural integrity checks failed.  
  
## User Action  
 To resolve this error, verify the structure of the interchange, ensuring that the group or transaction set headers and trailers are valid, and then resend the interchange.