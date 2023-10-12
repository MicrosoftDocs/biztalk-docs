---
description: "Learn more about: Single Sign-On: Event 10561"
title: "Single Sign-On: Event 10561"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10561
## Details  
  
| Field | Error Details |
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
