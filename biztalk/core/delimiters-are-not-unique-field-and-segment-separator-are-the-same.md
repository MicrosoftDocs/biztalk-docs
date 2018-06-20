---
title: "Delimiters are not unique, field and segment separator are the same | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1441434a-e969-4803-8e44-c7738d9b23ed
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Delimiters are not unique, field and segment separator are the same
## Details  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |          Delimiters are not unique, field and segment separator are the same           |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because the data element and segment separators were the same value. In an X12 interchange, the data element separator is the character in the fourth character position of the ISA segment and the segment terminator is the character in the last character position of the ISA segment. In an EDIFACT interchange, the data element separator is the character in the UNA2 field and the segment terminator is the character in the UNA6 field. Two separators with the same value can occur (but will cause an error condition) in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.  
  
## User Action  
 To resolve this error, change the value of either the data element or segment separator in the interchange, and then resubmit the interchange.