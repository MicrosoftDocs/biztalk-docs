---
description: "Learn more about: An End Element was found while looking for Start Element"
title: "An End Element was found while looking for Start Element"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# An End Element was found while looking for Start Element
## Details  
  
|     Field   |                      Error Details                                                                        |
|-----------------|---------------------------------------------------------------------------------------------------|
|  Product Name   |        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]         |
| Product Version |                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                     |
|    Event ID     |                                                 -                                                 |
|  Event Source   |      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI       |
|    Component    |                                            EDI Engine                                             |
|  Symbolic Name  |                             EndElementFoundWhenLookingForStartElement                             |
|  Message Text   | An EndElement with name {0} was found, while looking for StartElement with name {1}, at depth {2} |
  
## Explanation  
 This Error/Warning/Information event indicates that BizTalk Server could not process an incoming XML message (after parsing) or an outgoing XML message (before serialization) because the XML message failed validation. The XML message did not contain an end tag for a header or data element.  
  
## User Action  
 To resolve this error, add the appropriate end tag or trailer to the XML message, and then resend the message.
