---
description: "Learn more about: How to List the Properties of an Affiliate Application"
title: "How to List the Properties of an Affiliate Application | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fac15775-39d0-470e-b9d2-21b2d02e1de7
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# How to List the Properties of an Affiliate Application
The **displayapp** command shows the following information about the affiliate application. For more information about the properties for an affiliate application, see [SSO Affiliate Applications](../esso/sso-affiliate-applications.md).  
  
 The Single Sign-On (SSO) system obtains this information from the XML file that you used to update the affiliate application. For more information, see [How to Update the Properties of an Affiliate Application](../esso/how-to-update-the-properties-of-an-affiliate-application.md).  
  
### To display the properties of an affiliate application using the administration utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –displayapp <application name>`, where *\<application name>* is the name of the affiliate application that you want to display the properties for.  
  
### To display the properties of an affiliate application using the client utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is \<*install drive*>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient –displayapp <application name>`, where *\<application name>* is the name of the affiliate application that you want to display the properties for.  
  
## See Also  
 [Managing User Mappings](../esso/managing-user-mappings.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)
