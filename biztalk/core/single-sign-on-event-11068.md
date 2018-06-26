---
title: "Single Sign-On: Event 11068 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f09a1191-ae67-4156-a8a5-d24e4439fc68
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11068
## Details  
  
|                 |                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                      Enterprise Single Sign-On                                                                      |
| Product Version |                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                      |
|    Event ID     |                                                                                11068                                                                                |
|  Event Source   |                                                                               ENTSSO                                                                                |
|    Component    |                                                                                 N/A                                                                                 |
|  Symbolic Name  |                                                          SSO_ERROR_LOOKUP_CALLBACK_ACCESS_DENIED_NO_REMOTE                                                          |
|  Message Text   | Lookup server access denied. This SSO server is currently not configured to allow remote lookup. Use 'ssoconfig -remoteLookup yes' or the SSO Administration MMC.%r |
  
## Explanation  
 Lookup server access has been denied because the ENTSSO server is not configured to allow remote lookup.  
  
## User Action  
 To allow remote lookup, in the **Servers Snap-In**, **Advanced** tab, select **Allow Remote Lookup**.  
  
 For more information, see [How to Use the Servers Snap-in](../core/how-to-use-the-servers-snap-in.md).