---
description: "Learn about the requirements for using Single Sign-On (SSO) in the Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS)."
title: "SSO requirements for TIBCO EMS adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Requirements for Single Sign-On

## Overview

Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) provides Single Sign-On (SSO) support. An affiliate application created by Enterprise Single Sign-On tools represents a server system such as TIBCO EMS.  
  
To use Single Sign-On, you must have:  
  
- Microsoft BizTalk Server
  
- Visual Studio  
  
- Enterprise Single Sign-On  
  
- A server system that supports SSO  
  
  The isolated host should be configured as authentication trusted.
  
## Enable SSO  
  
1. In the **Transport Properties** window, select **Yes** for **Use SSO**.  
  
2. Select an appropriate affiliate application when specifying transport properties.  
  
    For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).  
  
    > [!NOTE]
    > After performing work using SSO, remember to reset any Web-Sharing folder to **Do not share**. Applications that use that folder will not update or uninstall correctly if the folder is shared because it is considered to be in use.  
  
## See Also
  
[Secure the adapter](../core/security-in-biztalk-adapter-for-tibco-ems.md)
