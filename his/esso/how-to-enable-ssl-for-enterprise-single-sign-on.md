---
description: "Learn more about: How to Enable SSL for Enterprise Single Sign-On"
title: "How to Enable SSL for Enterprise Single Sign-On"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Enable SSL for Enterprise Single Sign-On
Use the following command to enable Secure Sockets Layer (SSL) between all the Enterprise Single Sign-On (SSO) servers and the Credential database.  
  
### To enable SSL for Enterprise Single Sign-On  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –setssl <yes/no>`, where \<*yes/no*> indicates whether you want to enable SSL in the SSO system.  
  
## See Also  
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)
