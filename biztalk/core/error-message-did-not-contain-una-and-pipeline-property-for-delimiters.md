---
title: "Message did not contain UNA and pipeline property for delimiters was incorrect format | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b761d820-e09d-4949-bb41-da9e66054c60
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message did not contain UNA and pipeline property for delimiters was incorrect format
## Details  
  
|                 |                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------|
|  Product Name   |     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]      |
| Product Version |                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                  |
|    Event ID     |                                              -                                              |
|  Event Source   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI    |
|    Component    |                                         EDI Engine                                          |
|  Symbolic Name  |                                EfactDelimiterIncorrectFormat                                |
|  Message Text   | Message did not contain UNA and pipeline property for delimiters was incorrect format '{0}' |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming EDIFACT interchange because it could not determine the separators required to process the interchange. This can occur if the interchange does not have a UNA segment and the EfactDelimiters pipeline property does not adequately define the separators.  
  
## User Action  
 To resolve this error, do one of the following:  
  
1.  Make sure that the interchange has a UNA segment that defines the separators for the interchange, and then resend the interchange.  
  
2.  Set the EfactDelimiters pipeline property for the send pipeline by opening the BizTalk Server Administration Console, right-clicking the receive location that will be receiving the interchange, clicking Properties, clicking the ellipsis for the pipeline, and then entering a string containing the values of the separators.