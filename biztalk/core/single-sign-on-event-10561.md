---
title: "Single Sign-On: Event 10561 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 770e6fc1-0854-4555-8f2a-5f199e3aaca7
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10561
## Details  
  
|                 |                                                                                                                                                                                                                                 |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                    Enterprise Single Sign-On                                                                                                    |
| Product Version |                                                                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                    |
|    Event ID     |                                                                                                              10561                                                                                                              |
|  Event Source   |                                                                                                             ENTSSO                                                                                                              |
|    Component    |                                                                                                               N/A                                                                                                               |
|  Symbolic Name  |                                                                                                  SSO_ERROR_BACKUP_FAILED_MEDIA                                                                                                  |
|  Message Text   | The file specified for backup of the master secrets must be on an NTFS file system or removable media.%r<br /><br /> File Name: %1%r<br /><br /> Client User: %2%r<br /><br /> Client Computer: %3%r<br /><br /> Error Code: %4 |
  
## Explanation  
 A backup was attempted using an invalid media, such as a FAT file. The file specified for backup of the master secrets must be on an NTFS file system or removable media.  
  
## User Action  
 Check the media format and make sure it is NTFS or removable.