---
title: "Defending Against Denial-of-Service Attacks | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, denial-of-service attacks"
  - "denial-of-service attacks"
ms.assetid: 63342d7a-a5df-4e11-9037-93175d8f7ea7
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Defending Against Denial-of-Service Attacks
Someone could start a denial-of-service attack against an installation of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] by stressing the RNIFReceive.aspx receive page. They could do so by sending large numbers of empty messages to that page. If left unchecked, such an attack could flood the event log with events published by the ASPX receive page.  
  
## Defending Against an Attack  
 To defend your server against denial-of-service attacks, it is recommended that you maintain the event log at a reasonable size and take steps to deal with excessive numbers of events. You can accomplish this by setting the maximum log size, selecting a way of overwriting events, or using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]® Management Instrumentation (WMI) to manage the size of the log. For more information, see Help for [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsWinSvrNoVersion](../../includes/btswinsvrnoversion-md.md)]™.  
  
## See Also  
 [Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md)