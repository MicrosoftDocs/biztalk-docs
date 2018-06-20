---
title: "How to Set the SSO Server Using the Client Utility | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications [SSO], selecting servers"
  - "managing [SSO applications], selecting servers"
  - "SSOClient [SSO], selecting servers"
ms.assetid: a0f1038c-60c9-4e9d-a730-1ecfa036743b
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set the SSO Server Using the Client Utility
Each time you use ssoclient, you must first point the user to the correct Single Sign-On server that contains their configuration information.  
  
### To set the SSO Server for a user using the client utility  
  
1. On the **Start** menu, click **Run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type <strong>ssoclient –server *\<Single Sign-On Server\></strong><em>, where \<</em>Single Sign-On Server\>* is the name of the Single Sign-On server the user wants to connect to.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [SSO Affiliate Applications](../core/sso-affiliate-applications.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)