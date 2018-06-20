---
title: "How to Display the SSO Database Information | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [SSO], viewing SSO database"
  - "SSO database, viewing"
  - "viewing, SSO database"
ms.assetid: 0ebadd2e-6ea5-460c-b0a8-f48589e6bf1c
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Display the SSO Database Information
You can view SSO database information by using the MMC Snap-In or the command line (ssomanage) utility.  
  
### To display the SSO database information using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Properties**.  
  
4.  Click the tabs on the  **System Properties** dialog box to view SSO database information.  
  
### To display the SSO database information using the command line  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage –displaydb**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To display the SSO database the SSO Server is connected to using the command line  
  
1. On the **Start** menu, click **Run**, and then type **cmd**.  
  
2. At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type **ssomanage –showdb**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
   The following table describes the values displayed by these procedures.  
  
|Property|Value|  
|--------------|-----------|  
|SQL Server|**\<SQL Server name\>**|  
|Single Sign-On database|**\<SQL Server database name\>**|  
|Single Sign-On Secret Server name|**\<Single Sign-On Server name\>**|  
|Single Sign-On Administrators account|Domain\account name|  
|Single Sign-On Affiliate Administrators account|Domain\account name|  
|Size of audit table for deleted applications (number of audit entries)|1,000 (default)|  
|Size of audit table for deleted user mappings (number of audit entries)|1,000 (default)|  
|Size of audit table for external credential lookups (number of audit entries)|1,000 (default)|  
|Ticket timeout (in minutes)|2 (default)<br /><br /> This value can be an integer from1 through 525,600|  
|Credential cache timeout (in minutes)|60 (default)|  
|Single Sign-On Status|Enabled/disabled|  
|Tickets allowed|Yes/no (default)|  
|Validate tickets|Yes (default)/no|  
  
## See Also  
 [How to Configure the SSO Tickets](../core/how-to-configure-the-sso-tickets.md)   
 [Using SSO](../core/using-sso.md)