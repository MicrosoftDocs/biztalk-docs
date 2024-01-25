---
description: "Learn more about: ISA segment needs to have a minimum length of 108"
title: "ISA segment needs to have a minimum length of 108"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ISA segment needs to have a minimum length of 108
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                               NseIsaSuffix1LFDescription                               |
|  Message Text   |          ISA segment needs to have a minimum length of 108, instance has {0}           |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the ISA segment in the interchange did not conform to the number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).  
  
## User Action  
 To resolve this error, make sure that each of the fields in the ISA segment (from ISA01 to ISA16) has the required minimum number of digits. You can see the minimum number of digits by opening the BizTalk Server Administration Console; opening the BizTalk Group node, the Applications node, the BizTalk EDI Application node, and then the schema node; opening the Microsoft.BizTalk.Edi.BaseArtifacts.X12ServiceSchema with the root node of ISA; and then clicking the Schema View.
