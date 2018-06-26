---
title: "Error encountered during instance generation--field can repeat but repetition delimiter has not been defined | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7a6783c-cb35-4ce8-9164-ec34ae500de1
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error encountered during instance generation--field can repeat but repetition delimiter has not been defined
## Details  
  
|                 |                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                   |
| Product Version |                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                               |
|    Event ID     |                                                           -                                                           |
|  Event Source   |                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                 |
|    Component    |                                                      EDI Engine                                                       |
|  Symbolic Name  |                                                           -                                                           |
|  Message Text   | Error encountered during instance generation. The field {0} can repeat but repetition delimiter has not been defined. |
  
## Explanation  
 This Error/Warning/Information event indicates that BizTalk Server could not generate an X12 message instance because the indicated field can repeat (as specified by the schema), but no repetition separator has been defined. This occurs when a field in the schema has minOccurs equal to more than 1, but a Standard identifier has been defined, rather than a Repetition separator. (For EDIFACT interchanges, a repetition separator is defined by default.)  
  
## User Action  
 To resolve this error, select Repetition separator rather than Standard identifier for ISA11 in the ISA Segment Definition page for the party as interchange receiver, and enter a character for the separator. If no party has been resolved for the interchange, define the repetition separator in the ISA Segment Definition page of the global properties (for X12 interchanges).