---
description: "Learn more about: Best Practices for Backing Up and Restoring Databases"
title: "Best Practices for Backing Up and Restoring Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "best practices, maintaining"
  - "restoring, best practices"
  - "best practices, backing up"
  - "backing up, restoring"
  - "backing up, best practices"
  - "maintaining, best practices"
  - "best practices, restoring"
ms.assetid: 649ca56b-3cc1-49ad-9f74-ba1521e65ee1
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for Backing Up and Restoring Databases
Review the following best practices to help ensure that you can backup and restore your BizTalk Server databases.  
  
-   **Develop backup and restore strategies and test them.**  
  
     With a good plan, you can quickly recover your data if it is lost due to hardware failure.  
  
-   **Manage disk space and archive previous backup files.**  
  
     The Backup BizTalk Server job does not delete outdated backup files, so you need to manage those backup files to conserve disk space. After you have created a new full backup of your databases, you should move the outdated backup files onto an archival storage device to reclaim space on the primary disk.  
  
-   **Do not store backups on the same computer or disk that you are backing up.**  
  
     You should specify a computer or disk for your backup that is different from the computer with the original data. Otherwise, you will lose all of your data if the hardware fails.  
  
-   **Retain copies.**  
  
     Keep at least three copies of the media. Keep at least one copy off-site in a properly controlled environment.  
  
-   **Perform trial restorations.**  
  
     Perform a trial restoration at least once a month to verify that your files were properly backed up. A trial restoration can uncover hardware problems that do not show up when you verify that your software is functioning properly. Do not wait until your hard disk fails to see if you can restore your system and databases.  
  
-   **Secure devices and media.**  
  
     Secure both the storage device and the backup media. It is possible for someone to access the data from a stolen medium by restoring the data to another server for which they are an administrator.  
  
-   **Monitor the backup and restore process.**  
  
     To ensure that the backup and restore process was successful, you should monitor the SQL Server Agent jobs used to backup and restore BizTalk Server.  
  
## See Also  
 [Backing Up and Restoring the BizTalk Server Databases](../core/backing-up-and-restoring-the-biztalk-server-databases.md)
