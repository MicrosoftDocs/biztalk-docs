---
title: "The group receiver settings are not configured for agreement of batch | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57b205e9-aaab-43d1-b373-17d206957814
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The group receiver settings are not configured for agreement of batch
## Details  
  
|                 |                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                          |
| Product Version |                                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                      |
|    Event ID     |                                                                  -                                                                  |
|  Event Source   |                       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                        |
|    Component    |                                                           Batching Engine                                                           |
|  Symbolic Name  |                                                      GroupReceiverNotSelected                                                       |
|  Message Text   | The group receiver settings are not configured for agreement of batch {0}. This needs to be configured before batching can proceed. |
  
## Explanation  
 This Error/Warning/Information event indicates that one of two conditions has occurred:  
  
-   The batching orchestration could not validate a batch element that it has received because the UNB1.1 field (for an EDIFACT-encoded interchange) that contains the encoding syntax was not set.  
  
-   The batching orchestration could not create the envelope settings for the batch element because the header properties were not complete (ISA, GS, and ST properties for an X12 interchange or UNA, UNB, UNG, and UNH properties for an EDIFACT interchange).  
  
## User Action  
 To resolve this error, do one of the following:  
  
-   If the batching orchestration could not validate a batch element that it has received because the encoding syntax was not set, set the encoding syntax for the UNB1.1 field in the UNB Segment Definition page of the EDI Properties dialog box.  
  
-   If the batching orchestration could not create the envelope settings for the batch element because the header properties were not complete, ensure that the ISA, GS, and ST properties for an X12 interchange are set or that the UNA, UNB, UNG, and UNH properties for an EDIFACT interchange are set.