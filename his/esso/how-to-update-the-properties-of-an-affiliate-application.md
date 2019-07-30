---
title: "How to Update the Properties of an Affiliate Application | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7a793f1-abf6-4378-a4ee-f1e174f4e29f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Update the Properties of an Affiliate Application
Use the MMC Snap-In or the **updateapps** command to update one or more application properties, as specified by the XML file. You must be an affiliate administrator to perform this task. The following is an example XML file that lists the fields you can update.  
  
```  
<SSO>  
<application name="SSOApplication">  
<description>An SSO Application</description>  
<contact>someone@companyname.com</contact>  
<appUserAccount>DomainName\AppUserGroup</appUserAccount>  
<appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>  
<flags allowTickets="no" validateTickets="yes"  timeoutTickets="yes" enableApp="no" />  
</application>  
</SSO>  
  
```  
  
 After you create an affiliate application, you cannot modify the following properties:  
  
-   Name of the affiliate application.  
  
-   Fields associated with the affiliate application.  
  
-   Affiliate application type (host group, individual, or configuration store).  
  
-   Administration account same as affiliate administrators group. (Specifying this flag will always use the affiliate administrators group as the administrator account for this affiliate application).  
  
    > [!IMPORTANT]
    >  You can use local accounts for the administration account and user account by setting the allowLocalAccounts flag to yes. However, you can only use this flag in single-computer scenarios.  
  
    > [!NOTE]
    >  You must be an SSO administrator, SSO affiliate administrator, or application administrator to perform this task.  
  
    > [!NOTE]
    >  You must be an SSO administrator to modify the ticketing flags (validateTickets and timeoutTickets).  
  
    > [!NOTE]
    >  You must be an SSO administrator or an SSO affiliate administrator to modify the application administration account.  
  
### To update the properties of an affiliate application using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click the affililate application, and then click **Update**.  
  
### To update the properties of an affiliate application using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –updateapps <application file name>`, where the *application file name* is the XML file.  
  
## See Also  
 [SSO Affiliate Applications](../esso/sso-affiliate-applications.md)   
 [How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md)   
 [Managing User Mappings](../esso/managing-user-mappings.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)