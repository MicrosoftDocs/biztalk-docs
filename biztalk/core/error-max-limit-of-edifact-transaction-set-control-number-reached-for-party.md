---
title: "Max limit of acceptable Edifact transaction set control number has reached for party | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a64cc5d3-a845-4044-9c6e-879ecda15fce
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Max limit of acceptable Edifact transaction set control number has reached for party
## Details  
  
|                 |                                                                                                                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                        |
| Product Version |                                                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                    |
|    Event ID     |                                                                                                -                                                                                                 |
|  Event Source   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                      |
|    Component    |                                                                                            EDI Engine                                                                                            |
|  Symbolic Name  |                                                                                   GlobalEdifactUnhNumberError                                                                                    |
|  Message Text   | Max limit of acceptable Edifact transaction set control number has reached for party {0}. Reset counter by navigating to Party in receiver role screen, field UNH 1 in Partner Agreement manager |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process the outgoing interchange because the transaction set control number in the UNH1 field specified in the party settings, specifically the reference number in field UNH1.2, was greater than the maximum allowable value. The maximum allowable value for the transaction set control number depends upon the values of the three fields in UNH1. The maximum number of characters is 14 for the reference number in field UNH1.2, 13 for the prefix in UNH1.1 and 13 for the suffix in UNH1.3, and 14 for all three fields combined.  
  
## User Action  
 To resolve this error, reset the reference number field (UNH1.2) of the transaction set control number, as follows:  
  
1.  In the EDI Properties dialog box for the party resolved for the interchange, open the UNG and UNH Segment Definition page.  
  
2.  Click the Edit field associated with the UNH1 field.  
  
3.  Set the middle field of the transaction set control number (the reference number in UNH1.2) to a new value such that the field has an acceptable number of digits.