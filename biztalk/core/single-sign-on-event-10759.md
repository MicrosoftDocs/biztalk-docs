---
title: "Single Sign-On: Event 10759 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5347f3d6-d31a-4c00-a64c-c0b0f680de88
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10759
## Details  
  
|                 |                                                                                                                   |
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