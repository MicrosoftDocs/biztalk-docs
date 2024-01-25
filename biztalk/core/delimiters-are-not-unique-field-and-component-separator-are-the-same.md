---
description: "Learn more about: Delimiters are not unique, field and component separator are the same"
title: "Delimiters are not unique, field and component separator are the same"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Delimiters are not unique, field and component separator are the same

## Details  
  
|       Field     |                           Error Details                                                |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |         Delimiters are not unique, field and component separator are the same          |
  
## Explanation
  
This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because the data element and component separators were the same value. In an X12 interchange, the data element separator is the character in the fourth character position of the ISA segment and the component separator is the character in the ISA16 field. In an EDIFACT interchange, the data element separator is the character in the UNA2 field and the component separator is the character in the UNA1 field. Two separators with the same value can occur (but will cause an error condition) in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.  
  
## User Action
  
To resolve this error, change the value of either the data element or component separators, and then resubmit the interchange.
