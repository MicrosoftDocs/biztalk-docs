---
title: "How to Set the Enterprise SSO Server Using the Client Utility | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68e0c19b-eeb8-4254-91aa-5be518b5fcf5
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Set the Enterprise SSO Server Using the Client Utility
Each time you use **ssoclient**, you must first point the user to the correct Single Sign-On (SSO) server that contains their configuration information.  
  
### To set the SSO Server for a user using the client utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient –server <Single Sign-On Server>`, where *\<Single Sign-On Server>* is the name of the Single Sign-On server that the user wants to connect to.  
  
## See Also  
 [SSO Affiliate Applications](../esso/sso-affiliate-applications.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)