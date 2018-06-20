---
title: "SSO Requirements for TIBCO Rendevous adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d5c406b-f548-4df0-8644-fdf6a812a989
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Requirements for Single Sign-On

## Prerequisites
To use Single Sign-On (SSO), you must have the following:  
  
-   Microsoft BizTalk Server
  
-   Visual Studio  
  
-   Enterprise Single Sign-On  
  
-   A server system that supports SSO  
  
-   The isolated host should be configured as Authentication Trusted.  
  
## Enable SSO  
  
1. In the **Transport Properties** window, select **Yes** for **Use SSO**.  
  
2. Select an appropriate affiliate application when specifying transport properties.  
  
   For more information, see [Creating Affiliate Applications](../core/creating-affiliate-applications1.md).  
  
> [!NOTE]
>  After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**. Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.  
  
## See Also  
[Security](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)