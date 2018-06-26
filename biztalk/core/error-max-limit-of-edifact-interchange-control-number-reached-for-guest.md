---
title: "Max limit of acceptable Edifact interchange control number has reached for Guest settings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5d2dcc0-61fd-47c9-9339-8a85319c5398
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Max limit of acceptable Edifact interchange control number has reached for Guest settings
## Details  
  
|                 |                                                                                                                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                               |
| Product Version |                                                                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                           |
|    Event ID     |                                                                                                       -                                                                                                       |
|  Event Source   |                                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                             |
|    Component    |                                                                                                  EDI Engine                                                                                                   |
|  Symbolic Name  |                                                                                          GlobalEdifactUnbNumberError                                                                                          |
|  Message Text   | Max limit of acceptable Edifact interchange control number has reached for Guest settings. Reset counter by navigating to Global configuration receiver role screen, field UNB 5 in Partner Agreement manager |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process the outgoing interchange because the interchange control number in the ISA13 field specified in the global settings, specifically the reference number in field UNB5.2, was greater than the maximum allowable value. The maximum allowable value for the interchange control number depends upon the values of the three fields in UNB5. The maximum number of characters is 14 for the reference number in field UNB5.2, 13 for the prefix in UNB5.1 and 13 for the suffix in UNB5.3, and 14 for all three fields combined.  
  
## User Action  
 To resolve this error, reset the reference number field (UNB5.2) of the interchange control number, as follows:  
  
1.  In the EDI Global Properties dialog box, open the UNB Segment Definition page.  
  
2.  Click the Edit field associated with the UNB5 field.  
  
3.  Set the middle field of the interchange control number (the reference number in UNB5.2) to a new value such that the field has an acceptable number of digits.