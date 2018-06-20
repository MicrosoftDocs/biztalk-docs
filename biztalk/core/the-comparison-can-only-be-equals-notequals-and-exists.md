---
title: "The Comparison can only be Equals, NotEquals and Exists | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aad902a2-d0dc-4d91-87a7-a6305e2f40e0
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Comparison can only be Equals, NotEquals and Exists
## Details  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                 Err_InvalidComparision                                 |
|  Message Text   |                The Comparison can only be Equals, NotEquals and Exists.                |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide to Batch a message.  
  
## User Action  
 To resolve this error, ensure that the filter provided in Active batches doesn’t specify an operator  other than Equals, NotEquals and Exists for XSD types that don’t support other operations.