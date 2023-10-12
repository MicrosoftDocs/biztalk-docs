---
description: "Learn more about: Corrupt Backup Files"
title: "Corrupt Backup Files"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Corrupt Backup Files
A backup file may become corrupt, damaged, or missing. If this occurs, at least one file cannot be restored. The restore job on the system that suffered the failure searches for the next valid full backup set. In most cases it will be necessary to force a full backup on the source system. If no such set exists, the restore job fails and each subsequent run also fails until a valid full backup set arrives. If a set does exist, it is used to repair the environment.  
  
> [!NOTE]
>  Due to the manner in which [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] writes backup data to a file, it is possible that [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] will report successful completion even if the backup failed during the actual writing of the data. This scenario primarily occurs when the disk being written to is not local to the computer and a network failure or interruption occurs. As a general precaution, if a network failure occurs while the backup job is running, force a full backup after the network connectivity problem is resolved.  
  
## See Also  
 [Troubleshooting Log Shipping](../technical-guides/troubleshooting-log-shipping.md)
