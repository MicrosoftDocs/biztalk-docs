---
description: "Learn more about: Single Sign-On: Event 11020"
title: "Single Sign-On: Event 11020"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11020
## Details  
  
| Field | Error Details|
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                                        Enterprise Single Sign-On                                                                                                                                                                        |
| Product Version |                                                                                                                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                        |
|    Event ID     |                                                                                                                                                                                  11020                                                                                                                                                                                  |
|  Event Source   |                                                                                                                                                                                 ENTSSO                                                                                                                                                                                  |
|    Component    |                                                                                                                                                                                   N/A                                                                                                                                                                                   |
|  Symbolic Name  |                                                                                                                                                          SSO_INFO_WINDOWS_TO_WINDOWS_MAPPING_CONFLICT_ALLOWED                                                                                                                                                           |
|  Message Text   | A Windows password change will cause a different Windows account to be changed.%r<br /><br /> This is allowed because the adapter for this external system is configured to allow mapping conflicts.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> External Account: %3%r<br /><br /> Windows Account 1: %4%r<br /><br /> Windows Account 2: %5 |
  
## Explanation  
 This is an informational message stating that a Windows password change will cause a different Windows account to be changed.  
  
## User Action  
 You should confirm immediately that this change was made with your knowledge and authorization. If so, no action is required. If not, find out where the change initiated, and confirm that it was a location safely within the system.
