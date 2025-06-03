---
description: "Learn more about: How to Update the Properties of an Affiliate Application"
title: "How to Update the Properties of an Affiliate Application"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Update the Properties of an Affiliate Application
You can use the MMC Snap-In or this command to update one or more application properties, as specified by the XML file. You must be an Affiliate Administrator to perform this task. The following is an example XML file that lists the fields you can update.  
  
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
  
-   Name of the affiliate application  
  
-   Fields associated with the affiliate application  
  
-   Affiliate application type (host group, individual, or configuration store)  
  
-   Administration account same as affiliate administrators group. (Specifying this flag will always use the affiliate administrators group as the administrator account for this affiliate application)  
  
> [!IMPORTANT]
>  You can use local accounts for the administration account and user account by setting the allowLocalAccounts flag to yes. However, you can only use this flag in single-computer scenarios.  
  
> [!IMPORTANT]
>  You must be an SSO administrator, SSO affiliate administrator, or application administrator to perform this task.  
  
> [!IMPORTANT]
>  You must be an SSO administrator to modify the ticketing flags (validateTickets and timeoutTickets).  
  
> [!IMPORTANT]
>  You must be an SSO administrator or an SSO affiliate administrator to modify the application administration account.  
  
### To update the properties of an affiliate application using the MMC Snap-In  
  
1.  On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click the affililate application, and then click **Update**.  
  
### To update the properties of an affiliate application using the command line  
  
1.  On the **Start** menu, click **run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage –updateapps \<application file name\>**, where the application file name is the XML file.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [SSO Affiliate Applications](../core/sso-affiliate-applications.md)   
 [How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md)   
 [Managing User Mappings](../core/managing-user-mappings.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)
