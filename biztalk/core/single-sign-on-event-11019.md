---
title: "Single Sign-On: Event 11019 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ec07b00-d567-4518-89eb-340e4f92429b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11019
## Details  
  
|                 |                                                                                                                                                                                                                                                                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                            Enterprise Single Sign-On                                                                                                                                                             |
| Product Version |                                                                                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                            |
|    Event ID     |                                                                                                                                                                      11019                                                                                                                                                                       |
|  Event Source   |                                                                                                                                                                      ENTSSO                                                                                                                                                                      |
|    Component    |                                                                                                                                                                       N/A                                                                                                                                                                        |
|  Symbolic Name  |                                                                                                                                                      SSO_PS_WARN_NOT_IN_GROUP_DELETE_FAILED                                                                                                                                                      |
|  Message Text   | The mapping is not valid because the Windows account is not in the Application Users account for the application. Failed to delete the mapping. The mapping will be ignored.%r<br /><br /> Tracking ID: %1%r<br /><br /> Windows Account: %2%r<br /><br /> Application Name: %3%r<br /><br /> Application Users: %4%r<br /><br /> Error Code: %5 |
  
## Explanation  
 Either the Windows account specified was never a part of the Application Users account for this application, or it was at one time, but has been changed or removed. The mapping has not been deleted.  
  
## User Action  
 Check the password sync account information for your system, and make sure your information is valid. Then recreate the mapping. Note that using the Create Mapping Wizard reduces the risk of invalid mapping information. You can delete the failed mapping. If you do not delete it, it will be ignored.