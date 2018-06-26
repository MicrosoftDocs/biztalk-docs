---
title: "Max limit of acceptable X12 transaction set control number has reached for Guest settings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5a4aa5c-13a7-4234-916e-562b52644c51
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Max limit of acceptable X12 transaction set control number has reached for Guest settings
## Details  
  
|                 |                                                                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                             |
| Product Version |                                                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                         |
|    Event ID     |                                                                                                     -                                                                                                      |
|  Event Source   |                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                           |
|    Component    |                                                                                                 EDI Engine                                                                                                 |
|  Symbolic Name  |                                                                                           GlobalX12TsNumberError                                                                                           |
|  Message Text   | Max limit of acceptable X12 transaction set control number has reached for Guest settings. Reset counter by navigating to Global configuration sender role screen, field ST 2 in Partner Agreement manager |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the transaction set control number in the ST02 field specified in the global settings, specifically the reference number in field ST02.2, was greater than the maximum allowable value. The maximum allowable value for the transaction set control number depends upon the values of the three fields in ST02. The maximum number of characters is 9 for the reference number in field UNH1.2, 8 for the prefix in UNH1.1 and 8 for the suffix in UNH1.3, and 9 for all three fields combined.  
  
## User Action  
 To resolve this error, reset the reference number field (ST02.2) of the transaction set control number, as follows:  
  
1.  In the EDI Global Properties dialog box, open the GS and ST Segment Definition page.  
  
2.  Click the Edit field associated with the ST02 field.  
  
3.  Set the middle field of the group control number (the reference number in ST02.2) to a new value such that the field has an acceptable number of digits.