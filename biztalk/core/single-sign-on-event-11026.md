---
description: "Learn more about: Single Sign-On: Event 11026"
title: "Single Sign-On: Event 11026"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11026
## Details  
  
| Field | Error Details|
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                Enterprise Single Sign-On                                                                                                                                |
| Product Version |                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                |
|    Event ID     |                                                                                                                                          11026                                                                                                                                          |
|  Event Source   |                                                                                                                                         ENTSSO                                                                                                                                          |
|    Component    |                                                                                                                                           N/A                                                                                                                                           |
|  Symbolic Name  |                                                                                                                             SSO_WARN_EXISTING_GROUP_MAPPING                                                                                                                             |
|  Message Text   | A new group mapping could not be created because there is a conflict with an existing mapping. Please delete the existing mapping and try again.%r<br /><br /> Existing Mapping: %1%r<br /><br /> New Mapping: %2%r<br /><br /> External Account: %3%r<br /><br /> Application Name: %4 |
  
## Explanation  
 The most likely cause is that your system is using an old version of Enterprise Single Sign-On, and old group applications.  
  
## User Action  
 Delete and recreate the mapping as suggested in the warning. If this fails, you may need to upgrade to a more recent version of Enterprise Single Sign-On.
