---
title: "Single Sign-On: Event 10843 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 847e464e-5733-4703-905f-d44a4c4f5cc3
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10843
## Details  
  
|                 |                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                      Enterprise Single Sign-On                                                                      |
| Product Version |                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                      |
|    Event ID     |                                                                                10843                                                                                |
|  Event Source   |                                                                               ENTSSO                                                                                |
|    Component    |                                                                                 N/A                                                                                 |
|  Symbolic Name  |                                                                         ENTSSO_E_NO_SECRET2                                                                         |
|  Message Text   | Cannot perform encryption or decryption because the secret is not available from the master secret server. See the event log (on computer ‘%1’) for related errors. |
  
## Explanation  
 Access is denied.  
  
## User Action  
 Either the master secret server is off-line, or the master secret server is missing the required master secret. See the event log on the specified computer for related errors.