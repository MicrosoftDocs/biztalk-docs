---
description: "Learn more about: Character set not supported because the encoding information in UNB1.1 does not match the actual encoding"
title: "Character set not supported because the encoding information in UNB1.1 does not match the actual encoding"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Character set not supported because the encoding information in UNB1.1 does not match the actual encoding
## Details  
  
|    Field             |    Error Details                                                                                                                                                 |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                  |
| Product Version |                                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                              |
|    Event ID     |                                                                          -                                                                          |
|  Event Source   |                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                |
|    Component    |                                                                     EDI Engine                                                                      |
|  Symbolic Name  |                                                                          -                                                                          |
|  Message Text   | Character set not supported. It could be due to the fact that encoding information in UNB1.1 does not match the actual encoding of the interchange. |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming EDIFACT interchange because the characters used in the interchange did not conform to the character set identified in field UNB1.1 of the interchange.  
  
## User Action  
 To resolve this error, do one of the following:  
  
-   Change the characters used in the interchange so they conform to the character set specified in field UNB1.1 of the interchange.  
  
-   Change the character set specified in field UNB1.1 of the interchange, so all characters in the interchange are part of the character set.
