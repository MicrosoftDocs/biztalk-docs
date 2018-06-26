---
title: "Based on the specified delimiter set, no valid Digit could be found | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 08887f7d-8256-4de3-8db9-b890451521ff
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Based on the specified delimiter set, no valid Digit could be found
## Details  
  
|                 |                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------|
|  Product Name   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]           |
| Product Version |                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                       |
|    Event ID     |                                                   -                                                    |
|  Event Source   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI         |
|    Component    |                                               EDI Engine                                               |
|  Symbolic Name  |                                                   -                                                    |
|  Message Text   | Based on the specified delimiter set, no valid Digit could be found. Please use another delimiter set. |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI send pipeline could not find a valid digit when generating an outgoing interchange because a digit used in a field of the outgoing interchange was the same as a separator character.  
  
## User Action  
 To resolve this error, change the separator values used by the EDI send pipeline to create a message so that no separator character will be the same as a digit used in a field of the outgoing interchange. Do one of the following:  
  
-   For an X12 interchange being sent to a resolved party, change the separator settings in the ISA Segment Definition page for the party as interchange receiver.  
  
-   For an X12 interchange being sent to a party that has not been resolved, change the separator settings in the ISA Segment Definition global property page.  
  
-   For an EDIFACT interchange being sent to a resolved party, change the separator settings in the UNA Segment Definition page for the party as interchange receiver.  
  
-   For an EDIFACT interchange being sent to a party that has not been resolved, change the separator settings in the UNA Segment Definition global property page.