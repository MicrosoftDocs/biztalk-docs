---
title: "Config Lock and Out-of-Date Messages in the Status Bar1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19c9833d-7d5e-491d-b7f6-e4653175622c
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Config Lock and Out-of-Date Messages in the Status Bar
The SNA Manager will only lock the configuration file when you initiate a configuration change. If the lock is obtained, the status bar will flash 'CONFIG LOCK'. When you complete the change and save the configuration file, the lock will be released and the status bar will be cleared.  
  
 The tree pane will display **'[Out Of Date]'** on other servers in the domain. To refresh the status on the out-of-date servers, on the **Service** menu, click **Stop**, and then click **Start**. The status bar will display **'OUT OF DATE'** if SNA Manager is out-of-date. On the **File** menu, click **Refresh**.