---
title: "Requirements for Single Sign-On | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1111377-2fe1-4d65-ac0d-c89d2f1740b8
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Requirements for Single Sign-On
To use Single Sign-On (SSO), you must have the following software installed:  
  
-   Microsoft BizTalk Server
  
-   Visual Studio  
  
-   Enterprise Single Sign-On  
  
-   A Server System that supports SSO  
  
-   The isolated host should be configured as **Authentication Trusted**.  
  
## Enable SSO  
  
1. In the **Transport Properties** window, select **Yes** for **Use SSO**.  
  
2. Select an appropriate affiliate application when specifying transport properties.  
  
   For information about creating an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications4.md).  
  
> [!NOTE]
>  After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**. Applications using that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.  
  
## See Also  
 [Security in BizTalk Adapter for JD Edwards EnterpriseOne](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)