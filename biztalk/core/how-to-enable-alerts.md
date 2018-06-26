---
title: "How to Enable Alerts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Enable-Alerts command [BAM]"
  - "managing [BAM definitions], enabling alerts"
  - "alerts, enabling"
ms.assetid: 18f494b7-54fb-4aaf-89d1-7e3fe91f35c6
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Enable Alerts
Administrators use the **enable-alerts** command to enable all of the alerts on the specified view.  
  
### To enable an alert  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt. Press **ENTER**.  
  
3. Type **bm enable-alerts -View:\<view name\>**.  
  
   > [!NOTE]
   >  If you have exported a BAM configuration as XML, do not modify the XML related to alerts. If you change XML related to alerts and deploy the changes, bm.exe will detect the change and enable BAM alerts.  
  
4. Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)   
 [enter link description here](../core/how-to-disable-alerts.md)