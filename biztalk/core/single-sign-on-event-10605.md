---
description: "Learn more about: Single Sign-On: Event 10605"
title: "Single Sign-On: Event 10605"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10605
## Details  
  
| Field | Error Details |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                       Enterprise Single Sign-On                                                                       |
| Product Version |                                                      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                       |
|    Event ID     |                                                                                 10605                                                                                 |
|  Event Source   |                                                                                ENTSSO                                                                                 |
|    Component    |                                                                                  N/A                                                                                  |
|  Symbolic Name  |                                                                         SSO_ERROR_DTC_IMPORT                                                                          |
|  Message Text   | Could not import a DTC transaction. Please check that MSDTC is configured correctly for remote operation. See documentation for details.%r<br /><br /> Error Code: %1 |
  
## Explanation  
 There is a problem with the Microsoft Distributed Transaction Coordinator (MSDTC).  
  
## User Action  
 For help on MSDTC issues, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).
