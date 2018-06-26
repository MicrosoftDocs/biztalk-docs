---
title: "Single Sign-On: Event 11049 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 031ec1a6-4b2b-46b2-9dbb-5525d758651f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11049
## Details  
  
|                 |                                                                |
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