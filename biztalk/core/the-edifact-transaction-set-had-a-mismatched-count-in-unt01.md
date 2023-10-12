---
description: "Learn more about: The Edifact Transaction set had a mismatched count in UNT01"
title: "The Edifact Transaction set had a mismatched count in UNT01"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The Edifact Transaction set had a mismatched count in UNT01
## Details  
  
| Field | Error Details|
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                          |
| Product Version |                                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                      |
|    Event ID     |                                                                  -                                                                  |
|  Event Source   |                       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                        |
|    Component    |                                                             EDI Engine                                                              |
|  Symbolic Name  |                                                      EfactUnhUntCountMismatch                                                       |
|  Message Text   | The Edifact Transaction set had a mismatched count in UNT01. UNT01 was {0}, whereas it should have been {1}. It has been corrected. |
  
## Explanation  
 This Warning indicates that the UNT01 field, which is the segment count, did not match the number of segments in the transaction set. Either the value of UNT01 was changed or corrupted, or segments were added or deleted after the count was determined. The send pipeline reset the UNT01 field to the correct number of segments, and then sent the interchange.  
  
## User Action  
 No user action is necessary.
