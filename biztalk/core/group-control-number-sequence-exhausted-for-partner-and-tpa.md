---
title: "Group control number sequence exhausted for Partner and TPA | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf341f8d-02ec-4618-a980-c8ac90654b1a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Group control number sequence exhausted for Partner and TPA
## Details  
  
|                 |                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                      |
| Product Version |                                                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                  |
|    Event ID     |                                                                              -                                                                               |
|  Event Source   |                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                    |
|    Component    |                                                                          EDI Engine                                                                          |
|  Symbolic Name  |                                                              EdiControlNumberExhaustedForParty                                                               |
|  Message Text   | Group control number sequence exhausted for Partner '{1}' for the TPA '{2}'. Reset the sequence in {2} - EDI Properties using BizTalk Server Administration. |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was not able to process the document because the Group control range has been used up for the agreement in {2}.  
  
## User Action  
 To resolve this error, please tick the checkbox to reset the control number for the {2} agreement or increase the control number range or hit the reset button against the control number range specification in the agreement.