---
title: "Single Sign-On: Event 10555 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8af9c663-4aa8-4ca5-be63-d4461a2a8517
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10555
## Details  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10555                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                            N/A                             |
|  Symbolic Name  |          SSO_ERROR_SECRET_CALLBACK_ACCESS_DENIED           |
|  Message Text   | Secret server access denied.%r<br /><br /> Client User: %1 |
  
## Explanation  
 A message was sent to the server but the reply was blocked. This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions on the server.  
  
## User Action  
 Note the information in the error log and contact product support services.