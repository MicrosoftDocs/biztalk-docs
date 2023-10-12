---
description: "Learn more about: Unrecognized segment ID"
title: "Unrecognized segment ID"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Unrecognized segment ID
## Details  
  
|      Field      |                                  Error Details                                     |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  | EfactUnrecognizedSegmentIDDescription<br /><br /> X12UnrecognizedSegmentIDDescription  |
|  Message Text   |                                Unrecognized segment ID                                 |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because a segment in a transaction set in the interchange was not defined by the corresponding document schema.  
  
## User Action  
 To resolve this error, have the sender of the interchange remove the unrecognized segment and resend the interchange.
