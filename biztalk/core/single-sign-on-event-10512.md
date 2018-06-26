---
title: "Single Sign-On: Event 10512 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4edf0512-112d-40b8-9e29-7dd67f999b6d
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10512
## Details  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10512                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                            N\A                             |
|  Symbolic Name  |                   SSO_ERROR_LOADLIBRARY                    |
|  Message Text   |      Failed to load %1%r<br /><br /> Error code: %2.       |

## Explanation  
 This Error event indicates that the specified Dynamic Link Library (DLL) could not be loaded into the SSO server process. If the DLL is missing in the SSO installation directory, typically C:\Program Files\Common Files\Enterprise Single Sign-On, it may indicate that setup was not completed correctly, or that the DLL was deleted after setup was completed. If the DLL is present, then there could be a problem with the SSO service resolving the correct path to the DLL. Additionally, the DLL itself could be corrupted.  

## User Action  
 To resolve this error, do one or more of the following:  

- If a wider failure of setup is suspected it may be necessary to uninstall and reinstall the product.  

- If the single DLL is missing or corrupted, attempt to replace it and then restart the service.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)
