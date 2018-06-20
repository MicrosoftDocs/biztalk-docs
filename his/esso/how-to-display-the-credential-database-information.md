---
title: "How to Display the Credential Database Information | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c04ae538-921a-469e-9a4b-127de110f051
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Display the Credential Database Information
You can view Single Sign-On (SSO) credential database information by using the ssomanage command.  
  
### To display the SSO database information using the Microsoft Management Console (MMC) Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Properties**.  
  
4.  Click the tabs in the **SSO System Properties** dialog box to view SSO database information.  
  
### To display the Credential database information using the command line  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –displaydb`.  
  
### To display the Credential database that the SSO server is connected to  
  
1. Click **Start**, click **Run**, and then type `cmd`.  
  
2. At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
    The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type `ssomanage –showdb`.  
  
   The following table describes the values that are displayed.  
  
|Property|Value|  
|--------------|-----------|  
|SQL Server|\<*SQL Server name*>|  
|SQL Server database|\<*SQL Server database name*>|  
|Single Sign-On Secret Server name|\<*Single Sign-On Server name*>|  
|Single Sign-On Administrators account|Domain\account name|  
|Single Sign-On Affiliate Administrators account|Domain\account name|  
|Size of audit table for deleted applications (number of audit entries)|1000 (default)|  
|Size of audit table for deleted user mappings (number of audit entries)|1000 (default)|  
|Size of audit table for external credential lookups (number of audit entries)|1000 (default)|  
|Ticket timeout (in minutes)|2 (default)<br /><br /> This value can be an integer between 1 to 525600|  
|Credential cache timeout (in minutes)|60 (default)|  
|Single Sign-On Status|Enabled/disabled|  
|Tickets allowed|Yes/No (default)|  
|Validate tickets|Yes (default)/No|  
  
## See Also  
 [How to Configure the Enterprise Single Sign-On Tickets](../esso/how-to-configure-the-enterprise-single-sign-on-tickets.md)   
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)