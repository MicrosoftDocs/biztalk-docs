---
description: "Learn more about: Single Sign-On: Event 10565"
title: "Single Sign-On: Event 10565"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10565
## Details  
  
| Field | Error Details |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                           Enterprise Single Sign-On                                                                                           |
| Product Version |                                                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                           |
|    Event ID     |                                                                                                     10565                                                                                                     |
|  Event Source   |                                                                                                    ENTSSO                                                                                                     |
|    Component    |                                                                                                      N/A                                                                                                      |
|  Symbolic Name  |                                                                                       SSO_ERROR_SECRET_VALIDATE_FAILED                                                                                        |
|  Message Text   | The secret could not be loaded from the registry. The service account for the SSO service may have been changed or the secret may be corrupted. Restore the secret from a backup file.%r<br /><br /> MSID: %1 |
  
## Explanation  
 It is likely that an administrator in the system has changed the SSO Service account, making decryption impossible.  
  
## User Action  
 Find the person who changed the SSO Service account, and then restore the secret from a backup file. For more information on restoring the secret, see [Managing the Master Secret](../core/managing-the-master-secret.md).
