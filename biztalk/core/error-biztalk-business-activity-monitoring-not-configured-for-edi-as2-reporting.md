---
title: "BizTalk Business Activity Monitoring has not been configured for EDI-AS2 status reporting | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f46c1c8-2771-4b16-8fb1-71952792ac4a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Business Activity Monitoring has not been configured for EDI-AS2 status reporting
## Details  
  
|                 |                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                              |
| Product Version |                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                          |
|    Event ID     |                                                                      -                                                                      |
|  Event Source   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                            |
|    Component    |                                                                 AS2 Engine                                                                  |
|  Symbolic Name  |                                                                      -                                                                      |
|  Message Text   | BizTalk Business Activity Monitoring has not been configured for EDI/AS2 status reporting. Hence status reporting feature will be disabled. |
  
## Explanation  
 This Error/Warning/Information event indicates that EDI/AS2 status reporting is not enabled because Business Activity Monitoring (BAM) has not been configured through the BizTalk Configuration Wizard. The BAM infrastructure is a prerequisite for EDI/AS2 status reporting.  
  
## User Action  
 To resolve this error, run the BizTalk Configuration Wizard and configure Business Activity Monitoring.