---
description: "Learn more about: An End Element could not be found at depth"
title: "An End Element could not be found at depth"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# An End Element could not be found at depth
## Details  
  
|    Field             |       Error Details                                                                                 |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                               EndElementNotFoundAtDepth                                |
|  Message Text   |                     An End Element at depth {0} could not be found                     |
  
## Explanation  
 This Error/Warning/Information event indicates that BizTalk Server could not process the outgoing interchange because the XML message failed validation. The XML message did not contain an end tag for a header or data element.  
  
## User Action  
 To resolve this error, add the appropriate end tag or trailer to the XML message, and then resend.
