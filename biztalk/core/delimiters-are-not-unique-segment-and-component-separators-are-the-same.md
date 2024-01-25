---
description: "Learn more about: Delimiters are not unique, segment and component separators are the same"
title: "Delimiters are not unique, segment and component separators are the same"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Delimiters are not unique, segment and component separators are the same
## Details  
  
|     Field       |                                Error Details                                           |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |        Delimiters are not unique, segment and component separators are the same        |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because the segment terminator or the component separator were the same value. In an X12 interchange, the segment terminator is character in the last character position of the ISA segment and the component separator is the character in the ISA16 field. In an EDIFACT interchange, the segment terminator is the character in the UNA6 field and the component separator is the character in the UNA1 field. Two separators with the same value can occur (but will cause an error condition) in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.  
  
## User Action  
 To resolve this error, change the value of either the segment terminator or the component separator in the interchange, and then resubmit the interchange.
