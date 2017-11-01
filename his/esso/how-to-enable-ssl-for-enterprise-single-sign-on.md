---
title: "How to Enable SSL for Enterprise Single Sign-On | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7073ed1-bed1-4b4b-a371-542d24b2d3b3
caps.latest.revision: 3
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