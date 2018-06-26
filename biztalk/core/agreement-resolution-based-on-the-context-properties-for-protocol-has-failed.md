---
title: "Agreement Resolution based on the context properties for Protocol has failed | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58fccd84-579c-4b5e-872b-33730d4079e8
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Agreement Resolution based on the context properties for Protocol has failed
## Details  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                    AgreementResolutionContextPropertiesLookupFailed                    |
|  Message Text   |   Agreement Resolution based on the context properties for {0} Protocol has failed.    |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was not able to resolve to an Agreement based on the context properties that are provided by the customer.  
  
## User Action  
 To resolve this error, please provide the context properties as part of the BizTalk message such that Agreement Resolution can happen.