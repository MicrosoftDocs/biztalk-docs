---
description: "Learn more about: How to Enable SSL for SSO"
title: "How to Enable SSL for SSO"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Enable SSL for SSO
Use this command to enable Secure Sockets Layer (SSL) between all the Enterprise Single Sign-On (SSO) servers and the SSO database.  
  
### To enable SSL for Enterprise Single Sign-On  
  
1.  Click **Start**, click **Run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssoconfig –setSSL \<yes/no\>**, where \<**yes/no**\> indicates whether you want to enable SSL in the SSO system.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [Using SSO](../core/using-sso.md)
