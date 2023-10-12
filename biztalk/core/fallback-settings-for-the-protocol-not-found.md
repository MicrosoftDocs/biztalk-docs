---
description: "Learn more about: Fallback Settings for the Protocol not found"
title: "Fallback Settings for the Protocol not found"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Fallback Settings for the Protocol not found
## Details  
  
| Field | Error Details | 
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                      AgreementResolutionFallbackSettingsNotFound                       |
|  Message Text   |                   Fallback Settings for the {0} Protocol not found.                    |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was able to resolve to an agreement and has been redirected to Fallback settings and found that the fallback settings were not there for the particular protocol.  
  
## User Action  
 To resolve this error, please configure the fallback settings for the particular protocol.
