---
description: "Learn more about: Checklist: Backup and Restore"
title: "Checklist: Backup and Restore | Microsoft Docs"
ms.custom: ""
ms.date: "01/30/2018"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1d46a59-54f9-483e-9290-f4a9461006a7
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Backup and Restore
Perform the following steps before you have a hardware failure to ensure that you can restore your BizTalk Server system.  
  
## Back Up BizTalk Server  
  
|Step|Reference|  
|----------|---------------|  
|Keep a written record of all changes to your BizTalk Server system.||  
|Ensure that you have appropriate permissions to back up and restore BizTalk Server.|[Minimum Security User Rights](../core/minimum-security-user-rights.md)|  
|Learn how to back up and restore the BizTalk Server databases.|[Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md)|  
|Configure the Backup BizTalk Server job to back up the BizTalk Server databases.|[How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
|Configure the server where database backups will be stored.|[How to Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md)|  
|If you are using Business Activity Monitoring (BAM), back up the BAM databases.|[Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md)|  
|If you are using Enterprise Single Sign-on (SSO), back up the master secret.|[Managing the Master Secret](../core/managing-the-master-secret.md)|  
|Back up the BizTalk Server configuration file.|[How to Back Up The BizTalk Server Configuration](../core/how-to-back-up-the-biztalk-server-configuration.md)|  
|Back up the Enterprise Single Sign-On master secret.|[How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md)|  
|Back up the BAM portal application pools and virtual directories configuration information. If you are not using BAM, you do not need to perform this step.|[How to Back Up the BAM Portal](../core/how-to-back-up-the-bam-portal.md)|  
|Back up your BizTalk applications.|[Backing Up BizTalk Server Applications](../core/backing-up-biztalk-server-applications.md)|  
  
## Restore BizTalk Server  
  
|Step|Reference|  
|----------|---------------|  
|Restore your databases.|[How to Restore Your Databases](../core/how-to-restore-your-databases.md)|  
|Update references to the BAM database names.|[How to Back Up the BAM Analysis and Tracking Analysis Server Databases](../core/how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases.md)<br /><br /> [How to Update References to the BAM Analysis Server and Star Schema Database Names](../core/update-references-to-the-bam-analysis-server-and-star-schema-database-names.md)<br /><br /> [How to Update References to the BAM Archive Database Name](../core/how-to-update-references-to-the-bam-archive-database-name.md)<br /><br /> [How to Update References to the BAM Primary Import Database Name and Connection String](../core/update-references-to-bam-primary-import-database-name-and-connection-string.md)<br /><br /> [How to Update References to the BAM Notification Services Databases](../core/how-to-update-references-to-the-bam-notification-services-databases.md)<br /><br /> [How to Resolve Incomplete Activity Instances](../core/how-to-resolve-incomplete-activity-instances.md)|  
|If you are using Enterprise Single Sign-on, restore the master secret.|[Managing the Master Secret](../core/managing-the-master-secret.md)|  
|If the computer running BizTalk Server has failed, install BizTalk Server on the replacement computer.|[Installation Overview for BizTalk Server 2013 and 2013 R2](https://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)|  
|Restore the certificate store.<br /><br /> This step is required for Standard Edition. It is not required for other editions, such as Enterprise Edition, because the configuration process does this automatically.|[How to Restore the Certificate Store](../core/how-to-restore-the-certificate-store.md)|  
|Restore Enterprise Single Sign-On|[How to Recover Enterprise Single Sign-On](../core/how-to-recover-enterprise-single-sign-on.md)|  
|Restore the BizTalk group|[How to Recover the BizTalk Group](../core/how-to-recover-the-biztalk-group.md)<br /><br /> If you are restoring  Standard Edition, you must download a script that facilitates recovery of the server. Download [RestoreConfig.vbe](https://www.microsoft.com/download/details.aspx?id=7462).|  
|Restore the BizTalk Server configuration|[How to Recover the BizTalk Server Configuration](../core/how-to-recover-the-biztalk-server-configuration.md)|  
|If you are using BAM, you should restore the BAM alerts.<br /><br /> If you are not using BAM, you do not need to perform this step.|[How to Recover BAM Alerts](../core/how-to-recover-bam-alerts.md)|  
|If you are using BAM, you should restore the BAM portal.<br /><br /> If you are not using BAM, you do not need to perform this step.|[How to Recover the BAM Portal](../core/how-to-recover-the-bam-portal.md)|  
  
## See Also  
 [Backing Up and Restoring BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md)
