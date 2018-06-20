---
title: "Single Sign-On: Event 10604 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eea14ab1-5a89-4a62-b414-1bcb36ea339e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10604
## Details  
  
|                 |                                                                                                          |
|-----------------|----------------------------------------------------------------------------------------------------------|
|  Product Name   |                                        Enterprise Single Sign-On                                         |
| Product Version |                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                        |
|    Event ID     |                                                  10604                                                   |
|  Event Source   |                                                  ENTSSO                                                  |
|    Component    |                                                   N/A                                                    |
|  Symbolic Name  |                                      SSO_ERROR_SSOCSTX_OUT_OF_PROC                                       |
|  Message Text   | The 'ENTSSO Server' COM+ application is not configured correctly. It must be a COM+ library application. |
  
## Explanation  
 The COM+ application must be configured as a COM+ library application.  
  
## User Action  
 In the ENTSSO MMC Snap-In, expand the COM+ folder and locate your ENTSSO Server. Right-click the server, and then click Properties. Select Library Application instead of Server Application, and click OK.