---
description: "Learn more about: Single Sign-On: Event 10604"
title: "Single Sign-On: Event 10604"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10604
## Details  
  
| Field | Error Details |
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
