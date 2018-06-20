---
title: "Error encountered after processing Transaction Set(s) because the Start element of a Transaction set could not be found | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5380aee-1632-4cdf-98a1-aff87574ce4f
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error encountered after processing Transaction Set(s) because the Start element of a Transaction set could not be found
## Details  
  
|                 |                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| Product Version |                            [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                             |
|    Event ID     |                                                         -                                                         |
|  Event Source   |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI               |
|    Component    |                                                    EDI Engine                                                     |
|  Symbolic Name  |                                             InvalidEfactBiboXmlFormat                                             |
|  Message Text   | Error encountered after processing {0} Transaction Set(s). Start element of a Transaction set could not be found. |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI receive pipeline could not process an incoming transaction set because the receive pipeline could not find the ST or UNH header.  
  
## User Action  
 To resolve this error, contact the sender of the interchange, and have them ensure that the transaction set in error begins with an ST01 or UNH1 segment.