---
title: "How to Disable Alerts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "alerts, disabling"
  - "managing [BAM definitions], disabling alerts"
  - "Disable-Alerts command [BAM]"
ms.assetid: c5938bc2-1043-4633-8cad-02caf442f2e8
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Disable Alerts
Administrators use the **disable-alerts** command to disable all of the alerts on the specified view.  
  
### To disable an alert  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt. Press **ENTER**.  
  
3. Type **bm disable-alerts -View:\<view name\>**.  
  
   > [!NOTE]
   >  If you have exported a BAM configuration as XML, do not modify the XML related to alerts. If you change XML related to alerts and deploy the changes, bm.exe will detect the change and enable BAM alerts.  
  
4. Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)   
 [How to Enable Alerts](../core/how-to-enable-alerts.md)