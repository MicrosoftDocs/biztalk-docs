---
description: "Learn more about: Single Sign-On: Event 10759"
title: "Single Sign-On: Event 10759"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10759
## Details  
  
| Field | Error Details |
|-----------------|-------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                             Enterprise Single Sign-On                                             |
| Product Version |                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                             |
|    Event ID     |                                                       10759                                                       |
|  Event Source   |                                                      ENTSSO                                                       |
|    Component    |                                                        N/A                                                        |
|  Symbolic Name  |                                       ENTSSO_E_BACKUP_RESTORE_FAILED_MEDIA                                        |
|  Message Text   | The file specified for backup or restore of the master secrets must be on an NTFS file system or removable media. |
  
## Explanation  
 Only NTFS file systems or removable media can be secured.  
  
## User Action  
 Switch to either an NTFS file system of removable media to back up the master secret.
