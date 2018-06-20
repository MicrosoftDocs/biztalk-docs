---
title: "Single Sign-On: Event 10757 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24765a25-560b-4391-9839-a325894c679f
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10757
## Details  
  
|                 |                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------|
|  Product Name   |                                  Enterprise Single Sign-On                                   |
| Product Version |                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                  |
|    Event ID     |                                            10757                                             |
|  Event Source   |                                            ENTSSO                                            |
|    Component    |                                             N/A                                              |
|  Symbolic Name  |                                     ENTSSO_E_NO_MAPPING                                      |
|  Message Text   | The mapping does not exist. For Config Store applications, the config info has not been set. |
  
## Explanation  
 If this is an Individual or Group type application, then the mapping does not exist.  
  
 If this is a Config Store application, then the configuration data has not been set. This can occur when the SSO database has been reinitialized but the BizTalk Management database has not, or vice versa.  
  
## User Action  
 If this is an Individual or Group type application, create the desired mapping. For more information, see [How to Create User Mappings](../core/how-to-create-user-mappings.md).