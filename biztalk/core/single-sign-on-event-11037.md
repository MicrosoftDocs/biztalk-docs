---
title: "Single Sign-On: Event 11037 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b523ff56-112e-4798-97d2-b1b19e130ec7
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11037
## Details  
  
|                 |                                                                                                                                                                                                                                                       |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                               Enterprise Single Sign-On                                                                                                               |
| Product Version |                                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                               |
|    Event ID     |                                                                                                                         11037                                                                                                                         |
|  Event Source   |                                                                                                                        ENTSSO                                                                                                                         |
|    Component    |                                                                                                                          N/A                                                                                                                          |
|  Symbolic Name  |                                                                                                              SSO_INFO_PS_MAPPING_INVALID                                                                                                              |
|  Message Text   | External password change. The password was not changed for the external account because the mapping is no longer valid.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Application Name: %3%r<br /><br /> External Account: %4 |
  
## Explanation  
 The mapping is no longer a part of the Application Users group.  
  
## User Action  
 The message lists the name of the external account and application. You can use this information to find out why the mapping is no longer valid.