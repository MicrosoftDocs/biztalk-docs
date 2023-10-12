---
description: "Learn more about: The X12 Transaction set had a mismatched count in SE01"
title: "The X12 Transaction set had a mismatched count in SE01"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The X12 Transaction set had a mismatched count in SE01
## Details  
  
| Field | Error Details |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                       |
| Product Version |                                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                   |
|    Event ID     |                                                               -                                                               |
|  Event Source   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                     |
|    Component    |                                                          EDI Engine                                                           |
|  Symbolic Name  |                                                     X12StSeCountMismatch                                                      |
|  Message Text   | The X12 Transaction set had a mismatched count in SE01. SE01 was {0}, whereas it should have been {1}. It has been corrected. |
  
## Explanation  
 This Warning indicates that the number in the transaction set trailer (SE01 field) did not match the number of segments in the transaction set of the interchange. The send pipeline corrects the count in the SE01 field and posts the warning.  
  
## User Action  
 No action is necessary.
