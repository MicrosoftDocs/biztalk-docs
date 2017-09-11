---
title: "Requirements for Single Sign-On2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "enabling SSO"
  - "Single Sign-On, requirements"
  - "SSO, enabling"
  - "Single Sign-On, enabling"
  - "SSO requirements"
ms.assetid: ae4b5c1f-1718-4628-9159-2fb877498913
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Requirements for Single Sign-On
To use Single Sign-On (SSO), you need:  
  
-   [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   Enterprise Single Sign-On  
  
-   A Server System that supports SSO  
  
 The isolated host should be configured as authentication trusted.  
  
### To enable SSO  
  
1.  In the **Transport Properties** window, select **Yes** for **Use SSO**.  
  
2.  Select an appropriate affiliate application when specifying transport properties.  
  
 For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications2.md).  
  
> [!NOTE]
>  After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**. Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.  
  
## See Also  
 [Running SSO Projects](../core/running-sso-projects1.md)   
 [Using Single Sign-On](../core/using-single-sign-on2.md)