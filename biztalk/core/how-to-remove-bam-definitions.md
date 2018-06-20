---
title: "How to Remove BAM Definitions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "definitions [BAM], deleting"
  - "deleting, definitions [BAM]"
  - "managing [BAM definitions], deleting definitions"
  - "Remove-All command"
ms.assetid: a905f54b-7c55-49b8-809b-030ad65f3e46
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove BAM Definitions
Administrators use the **remove-all** command of the BAM Management utility to remove all views and underlying activity tables for a particular BAM definition file.  
  
### To Remove BAM definitions  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type **bm remove-all DefinitionFile:\<def file\>**.  
  
4. Press ENTER.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)