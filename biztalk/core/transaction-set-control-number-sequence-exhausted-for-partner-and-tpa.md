---
title: "Transaction set control number sequence exhausted for Partner and TPA | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 67f194ca-3e0f-4ad4-8bc8-88aa7e5193a7
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transaction set control number sequence exhausted for Partner and TPA
## Details  
  
|                 |                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                           |
| Product Version |                                                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                       |
|    Event ID     |                                                                                   -                                                                                    |
|  Event Source   |                                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                         |
|    Component    |                                                                               EDI Engine                                                                               |
|  Symbolic Name  |                                                                   EdiControlNumberExhaustedForParty                                                                    |
|  Message Text   | Transaction set control number sequence exhausted for Partner '{1}' for the TPA '{2}'. Reset the sequence in {2} - EDI Properties using BizTalk Server Administration. |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was not able to process the document because the Transaction set control range has been used up for the agreement in {2}.  
  
## User Action  
 To resolve this error, please tick the checkbox to reset the control number for the {2} agreement or increase the control number range or hit the reset button against the control number range specification in the agreement.