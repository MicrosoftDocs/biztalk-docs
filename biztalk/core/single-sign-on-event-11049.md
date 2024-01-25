---
description: "Learn more about: Single Sign-On: Event 11049"
title: "Single Sign-On: Event 11049"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11049
## Details  
  
| Field | Error Details | 
|-----------------|----------------------------------------------------------------|
|  Product Name   |                   Enterprise Single Sign-On                    |
| Product Version |   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]   |
|    Event ID     |                             11049                              |
|  Event Source   |                             ENTSSO                             |
|    Component    |                              N/A                               |
|  Symbolic Name  |                      SSO_ERROR_DTC_FAILED                      |
|  Message Text   | Could not get MSDTC. SSO requires MSDTC for correct operation. |
  
## Explanation  
 The ENTSSO system could not connect to the Microsoft Distributed Transaction Coordinator (MSDTC).  
  
## User Action  
 Check to see if MSDTC is currently operational.  
  
 For help on MSDTC issues, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).
