---
title: "Managing BAM Alert Execution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [BAM definitions], executing alerts"
  - "Notification Services, configuration files"
  - "BAM Management utility"
  - "alerts, executing"
ms.assetid: 44bb738e-fa2c-4b32-9e8d-e756d6c3778e
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing BAM Alert Execution
BAM Alert execution can be modified through three avenues, The BAM Portal, the BAM management utility, and the ProcessBamNSFiles.vbs script.  
  
## BAM Portal  
 Knowledge workers and administrators can modify the manner in which alerts are delivered by using the Alert Manager in the BAM portal. From the BAM portal, the Alert can be enabled or disabled, threshold levels can be modified, delivery locations can be modified, as well as other parameters the affect the execution of the alert.  
  
 For more information on modifying alerts, see [Alert Manager on the BAM Portal Page](../core/alert-manager-on-the-bam-portal-page.md) and [Alerts in the BAM Portal](../core/alerts-in-the-bam-portal.md).  
  
### BAM Management Utility  
 Administrators can use the BAM Management utility to enable, disable, and remove alerts.  
  
 For information on using the BAM Management Utility to mange alerts, the following topics:  
  
-   [How to Enable Alerts](../core/how-to-enable-alerts.md) 
  
-   [How to Disable Alerts](../core/how-to-disable-alerts.md)  
  
-   [How to Remove BAM Alerts](../core/how-to-remove-bam-alerts.md)  
  
### Modifying Notification Services Configuration Files  
 Administrators can use the ProcessBamNSFiles.vbs script to change the manner in which the Notification Services delivers alerts. For more information the Application Definition File (ADF) for Notification Services, see [http://go.microsoft.com/fwlink/?LinkId=127016](http://go.microsoft.com/fwlink/?LinkId=127016).  
  
 To modify the ADF associated with BAM you can follow these general steps:  
  
1. Run the script to obtain the current configuration and ADF files.  
  
2. Modify the files.  
  
3. Run the script to apply the changes.  
  
   For more information on the ProcessBamNSFiles.vbs script, see [BAM Command-Line Script for Notification Services Configuration Files](../core/bam-command-line-script-for-notification-services-configuration-files.md).  
  
## See Also  
 [Managing the BAM Portal](../core/managing-the-bam-portal.md)   
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)