---
description: "Learn more about: DLS Status Problems"
title: "DLS Status Problems2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01f12802-29ec-416f-8ce8-f44543478d2b
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# DLS Status Problems
If you get a message stating that no DLS service is available for a given server, you may not have access to the Registry for that server. For DLS status (or **dlsstat** on the command line) to display the available link services, you need to have access to the Registry on the system that you specify in DLS status.  
  
 To correct this problem, see if you have any access to the Registry keys in the HKEY_LOCAL_MACHINE window for a remote server: run **Regedit.exe** on the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer on which you ran dlsstat and connect to one of the remote computers. If everything in the Registry window is unavailable (dimmed out), dlsstat will not work properly. Make sure you have access to the Registry before running DLS status again.
