---
title: "Duplicate group control number found | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1badc033-42fd-4992-ad36-b53047ba7817
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Duplicate group control number found
## Details  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |                          Duplicate group control number found                          |

## Explanation  
 This Error/Warning/Information event indicates that the EDI receive pipeline could not process an incoming interchange because it had the same interchange, group, or transaction set control number as a previously received interchange. This will result in a failure as long as the appropriate duplicate control number checks are enabled.  

## User Action  
 To resolve this error, do one of the following:  

- Ensure that the interchange sent to BizTalk Server does not have the same group control number as a previous interchange, if the corresponding duplicate control number check is enabled.  

- Disable the duplicate group control number check. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the appropriate party, and open either the EDIFACT Interchange Processing Properties or the X12 Interchange Processing Properties dialog box for the party as an interchange sender. To disable a check for an EDIFACT interchange, clear the Check for duplicate UNG5 (Group control number) in interchange property. To disable a check for an X12 interchange, clear the Check for duplicate GS6 (Group control number) in interchange property.
