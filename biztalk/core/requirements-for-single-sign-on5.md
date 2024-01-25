---
description: "Learn about the requirements for enabling Single Sign-On (SSO)."
title: "Single Sign-on requirements"
ms.custom: ""
ms.date: "04/16/2021"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On requirements

To use Single Sign-On (SSO), you must have:  
  
- Microsoft BizTalk Server
  
- Visual Studio  
  
- Enterprise Single Sign-On  
  
- A Server System that supports SSO  
  
The isolated host should be configured as authentication trusted.  
  
## Enable SSO  
  
1. In the **Transport Properties** window, select **Yes** for **Use SSO**.  
  
2. Select an appropriate affiliate application when specifying transport properties.  
  
    For information about creating affiliate applications, see [Creating Affiliate Applications](../core/creating-affiliate-applications3.md).  
  
    > [!NOTE]
    > After performing work using SSO, remember to reset any **Web-Sharing** folder to **Do not share**. Applications using that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.  
  
## See Also

[Security in the adapter](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)
