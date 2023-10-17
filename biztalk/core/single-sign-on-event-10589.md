---
description: "Learn more about: Single Sign-On: Event 10589"
title: "Single Sign-On: Event 10589"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10589
## Details  
  
| Field | Error Details|
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                     Enterprise Single Sign-On                                                                                                                     |
| Product Version |                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                     |
|    Event ID     |                                                                                                                               10589                                                                                                                               |
|  Event Source   |                                                                                                                              ENTSSO                                                                                                                               |
|    Component    |                                                                                                                                N/A                                                                                                                                |
|  Symbolic Name  |                                                                                                                 SSO_ERROR_BACKUP_SECRET_REQUIRED                                                                                                                  |
|  Message Text   | The master secret has not been backed up. If you lose the master secret all the information stored in the SSO system will be lost permanently and your systems may fail to work correctly. Please use the SSO administration tools to back up your master secret. |
  
## Explanation  
 The master secret has not been backed up. If you lose the master secret all the information stored in the SSO system will be lost permanently and your systems may fail to work correctly.  
  
## User Action  
 For information on backing up the master secret, see [Managing the Master Secret](../core/managing-the-master-secret.md).
