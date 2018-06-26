---
title: "How to Create an Affiliate Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [SSO applications], creating"
  - "applications [SSO], creating"
  - "creating, applications [SSO]"
ms.assetid: d0967c4b-6201-416a-9d3a-23b5de5b83d6
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create an Affiliate Application
You can use the MMC Snap-In or this command to create one or more applications, as specified by the XML file. An example XML file for Windows Initiated SSO is:  
  
```  
<sso>  
<application name="SAP">  
<description>The SAP application</description>   
<contact>someone@example.com</contact>   
<appuserAccount>domain\AppUserAccount</appuserAccount>   
<appAdminAccount>domain\AppAdminAccount</appAdminAccount>   
<field ordinal="0" label="User Id" masked="no" />   
<field ordinal="1" label="Password" masked="yes" />   
<flags groupApp="no" configStoreApp="no" allowTickets="no" validateTickets="yes" allowLocalAccounts="no" timeoutTickets="yes" adminAccountSame="no" enableApp="no" />  
</application>  
</sso>  
  
```  
  
 After you create an affiliate application, you cannot modify the following properties:  
  
-   Name of the affiliate application  
  
-   Fields associated with the affiliate application  
  
-   Affiliate application type (host group, individual, or configuration store)  
  
-   Administration account same as affiliate administrators group. (Specifying this flag will always use the affiliate administrators group as the administrator account for this affiliate application)  
  
> [!IMPORTANT]
>  You can use local accounts for the administration account and user account by setting the allowLocalAccounts flag to yes. However, you should only use this flag in single-computer scenarios.  
  
> [!IMPORTANT]
>  You must be an SSO administrator or SSO affiliate administrator to perform this task.  
  
 After you create the affiliate application, you must enable it. For more information, see [How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md).  
  
### To create an affiliate application using the MMC Snap-In  
  
1.  On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **Affiliate Applications**, and then click **Create Application**.  
  
4.  Follow the instructions in the **Enterprise Single Sign-On Application Wizard**.  
  
### To create an affiliate application using the command line  
  
1. On the **Start** menu, click **run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type **ssomanage –createapps *\<application file name\>**<em>, where *\<application file name\></em> is the XML file.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [SSO Affiliate Applications](../core/sso-affiliate-applications.md)   
 [How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md)   
 [How to Delete an Affiliate Application](../core/how-to-delete-an-affiliate-application.md)   
 [Managing User Mappings](../core/managing-user-mappings.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)