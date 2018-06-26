---
title: "Single Sign-On: Event 10510 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4553ad4c-9553-4b8b-b3a3-72aed2a61202
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10510
## Details  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10510                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                            N\A                             |
|  Symbolic Name  |                  SSO_INFO_DLL_LOAD_FAILED                  |
|  Message Text   |   Failed to load %1. Check that this file is available.    |

## Explanation  
 This Information event indicates that the SSO service has failed to load the DLL.  

## User Action  
 To resolve this event, do one or more of the following:  

- Verify the DLL is located in the SSO installation directory, typically C:\Program Files\Common Files\Enterprise Single Sign-On. Your SSO installation directory may be different.  

- If the single DLL is missing or corrupted, attempt to replace it and then restart the service.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)
