---
title: "SNA Print Server Data Filter Programmer&#39;s Security Guide1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a51b8b7-2d83-4276-bf20-0ab20391ccff
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SNA Print Server Data Filter Programmer&#39;s Security Guide
The following topics discuss security as it applies to the APPC section of the [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] SDK.  
  
## Threats and mitigations for SNA Print Server Data Filter  
 Programmers who use the SNA Print Server Data Filter should be aware of the following security issue.  
  
### Store DLLs in a secure location  
 The DLLs which support the SNA Print Server Data Filter API can be configured by an administrator or developer. Because of this, the DLLs should be stored in a secure location, such as the default installation directory. If this location is customized by an administrator or developer the new location should also be secured.