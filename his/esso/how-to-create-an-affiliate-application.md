---
title: "How to Create an Affiliate Application | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3be483f8-2617-459e-9081-aab886c75d93
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Create an Affiliate Application
You can use the MMC Snap-In or the **createapps** command to create one or more applications, as specified by the XML file. The following is an example XML file for Windows-Initiated Single Sign-On (SSO):  
  
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
  
-   Name of the affiliate application.  
  
-   Fields associated with the affiliate application.  
  
-   Affiliate application type (host group, individual, or configuration store).  
  
-   Administration account same as affiliate administrators group. (Specifying this flag will always use the affiliate administrators group as the administrator account for this affiliate application.)  
  
> [!IMPORTANT]
>  You can use local accounts for the administration account and user account by setting the allowLocalAccounts flag to yes. However, you should only use this flag in single-computer scenarios.  
  
> [!IMPORTANT]
>  You must be an SSO administrator or SSO affiliate administrator to perform this task.  
  
> [!NOTE]
>  If you are performing the configuration on a Domain Controller, and the Domain Local scope groups are specified for Application Administrators or Application Users while creating Affiliate Applications, it is recommended that you enable the local account flag. To do this:  
  
- In the MMC Snap-in, select Allow local accounts for access accounts during the creation process.  
  
- From the command line, specify allowLocalAccounts=yes in the XML file for Affiliate Application creation.  
  
  After you create the affiliate application, you must enable it. For more information, see [How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md).  
  
### To create an affiliate application using the Microsoft Management Console (MMC) Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **Affiliate Applications**, and then click **New**.  
  
4.  Follow the instructions in the **Create New Affiliate Application** wizard.  
  
### To create an affiliate application using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –createapps <application file name>`, where *\<application file name>* is the XML file.  
  
## See Also  
 [SSO Affiliate Applications](../esso/sso-affiliate-applications.md)   
 [How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md)   
 [How to Delete an Affiliate Application](../esso/how-to-delete-an-affiliate-application.md)   
 [Managing User Mappings](../esso/managing-user-mappings.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)