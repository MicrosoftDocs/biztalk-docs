---
description: "Learn about the prerequisites for Single Sign-On (SSO) and how to enable it."
title: "SSO Requirements for TIBCO Rendevous adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On Requirements

## Prerequisites

To use Single Sign-On (SSO), you must have the following:  
  
- Microsoft BizTalk Server
  
- Visual Studio  
  
- Enterprise Single Sign-On  
  
- A server system that supports SSO  
  
- The isolated host should be configured as Authentication Trusted.  
  
## Enable SSO  
  
1. In the **Transport Properties** window, select **Yes** for **Use SSO**.  
  
2. Select an appropriate affiliate application when specifying transport properties.  
  
   For more information, see [Creating Affiliate Applications](../core/creating-affiliate-applications1.md).  
  
> [!NOTE]
> After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**. Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.  
  
## See Also
  
[Security](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)
