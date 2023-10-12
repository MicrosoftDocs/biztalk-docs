---
description: "Learn more about: Segment has trailing delimiter(s) at component or sub-component level"
title: "Segment has trailing delimiter(s) at component or sub-component level"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Segment has trailing delimiter(s) at component or sub-component level
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                      X12SeSegmentHasTrailingDelimiterDescription                       |
|  Message Text   |         Segment has trailing delimiter(s) at component or sub-component level          |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained trailing delimiters, but trailing delimiters were not enabled for the party as interchange sender.  
  
## User Action  
 To resolve this error, enable trailing separators as follows:  
  
1.  Open the BizTalk Server Administration Console, move to the Parties folder, and open the EDI Properties for the party.  
  
2.  Move to the Validation and ACK Generation page for X12 or EDIFACT, as appropriate.  
  
3.  Click "Allow trailing separators".
