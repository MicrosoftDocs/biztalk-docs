---
title: "Requirements for Single Sign-On1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JD Edwards EnterpriseOne adapters, Single Sign-On"
  - "SSO, requirements [JD Edwards EnterpriseOne adapters]"
  - "adapters [JD Edwards EnterpriseOne adapters], Single Sign-On"
  - "Single Sign-On, requirements [JD Edwards EnterpriseOne adapters]"
  - "Single Sign-On, enabling [JD Edwards EnterpriseOne adapters]"
ms.assetid: d1111377-2fe1-4d65-ac0d-c89d2f1740b8
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Requirements for Single Sign-On
To use Single Sign-On (SSO), you must have the following software installed:  
  
-   Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   Enterprise Single Sign-On  
  
-   A Server System that supports SSO  
  
-   The isolated host should be configured as **Authentication Trusted**.  
  
### To enable SSO  
  
1.  In the **Transport Properties** window, select **Yes** for **Use SSO**.  
  
2.  Select an appropriate affiliate application when specifying transport properties.  
  
 For information about creating an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications4.md).  
  
> [!NOTE]
>  After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**. Applications using that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.  
  
## See Also  
 [Using Single Sign-On](../core/using-single-sign-on1.md)