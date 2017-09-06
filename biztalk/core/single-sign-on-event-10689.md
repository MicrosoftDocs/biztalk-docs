---
title: "Single Sign-On: Event 10689 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79e4e31f-18e4-4f52-9466-18e58842942f
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10689
## Details  
  
|||  
|-|-|  
|Product Name|Enterprise Single Sign-On|  
|Product Version|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|Event ID|10689|  
|Event Source|ENTSSO|  
|Component|N\A|  
|Symbolic Name|SSO_ERROR_REPLAY_INCORRECT_RECORD_VERSION|  
|Message Text|Corruption was detected in the replay file.%r<br /><br /> Replay File: %1|  
  
## Explanation  
 This Error event indicates that SSO has re-established contact with the SSO database, but was unable to read the replay file because of corruption. If SSO cannot open a replay file, it will proceed to the next replay file (if there is one).  
  
 Replay files are used by password sync when the ENTSSO server cannot contact the SSO database. A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.  
  
## User Action  
 To resolve this error, do the following:  
  
-   Check System and Application event logs for associated events.  
  
-   Delete the replay file.  
  
 For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  
  
-   [Password Synchronization](../core/password-synchronization2.md)