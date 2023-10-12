---
description: "Learn more about: Max limit of acceptable X12 interchange control number has reached for Guest settings"
title: "Max limit of acceptable X12 interchange control number has reached for Guest settings"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Max limit of acceptable X12 interchange control number has reached for Guest settings
## Details  
  
| Field | Error Details |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                             |
| Product Version |                                                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                         |
|    Event ID     |                                                                                                     -                                                                                                      |
|  Event Source   |                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                           |
|    Component    |                                                                                                 EDI Engine                                                                                                 |
|  Symbolic Name  |                                                                                          GlobalX12IsaNumberError                                                                                           |
|  Message Text   | Max limit of acceptable X12 interchange control number has reached for Guest settings. Reset counter by navigating to Global configuration receiver role screen, field ISA 13 in Partner Agreement manager |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the interchange control number in the ISA13 field specified in the global settings was greater than the maximum allowable value. The maximum number of characters for the interchange control number is nine.  
  
## User Action  
 To resolve this error, reset the interchange control number, as follows:  
  
1.  In the EDI Global Properties dialog box, open the ISA Segment Definition page.  
  
2.  Click the Edit field associated with the ISA13 field.  
  
3.  Set the interchange control number to a new value such that the field has an acceptable number of digits.
