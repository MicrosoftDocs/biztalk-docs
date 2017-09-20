---
title: "Validating Passwords for Host Initiated SSO | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "passwords, host initiated [SSO]"
  - "host initiated SSO, passwords"
ms.assetid: 3cc1d68a-27ac-46ce-ba1e-21139a9df55e
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Validating Passwords for Host Initiated SSO
When an affiliate application for host initiated SSO is created, password validation for the non-Windows user is enabled by default. This means when applications call SSO to obtain the Windows user token to access resources, they must provide the non-Windows user account and the non-Windows password. If the password does not match the password in the SSO database for that non-Windows user, access is denied. If necessary, the password validation feature can be disabled for the affiliate application. The password validation feature applies to both individual and host group type affiliate applications for host initiated SSO.  
  
 An example XML file for Individual type host initiated SSO affiliate application is:  
  
```  
<sso>  
<application name="SAP">  
<description>The SAP application</description>   
<contact>someone@example.com</contact>   
<appuserAccount>domain\AppUserGroupAccount</appuserAccount>   
<appAdminAccount>domain\AppAdminGroupAccount</appAdminAccount>   
<field ordinal="0" label="User Id" masked="no" />   
<field ordinal="1" label="Password" masked="yes" />   
<flags groupApp="no"  configStoreApp="no" allowTickets="no" validateTickets="yes" allowLocalAccounts="no" timeoutTickets="yes" adminAccountSame="no" enableApp="no" />  
</application>  
</sso>  
  
```  
  
 In the case of individual applications for host initiated SSO, the appUserAccount is a group account that contains the list of Windows domain account users that have a 1 to 1 mapping with their corresponding non-Windows accounts.  
  
 An example XML file for host group type host initiated SSO affiliate application is:  
  
```  
<sso>  
<application name="SAP">  
<description>The SAP application</description>   
<contact>someone@example.com</contact>   
<appuserAccount>domain\AppUserAccount</appuserAccount>   
<appAdminAccount>domain\AppAdminGroupAccount</appAdminAccount>   
<field ordinal="0" label="User Id" masked="no" />   
<field ordinal="1" label="Password" masked="yes" />   
<flags  configStoreApp="no" allowTickets="no" validateTickets="yes" allowLocalAccounts="no" timeoutTickets="yes" adminAccountSame="no" enableApp="no" />  
</application>  
</sso>  
  
```  
  
 In group applications for host initiated SSO, the appUserAccount must be an individual user account. It is this account that all non-Windows accounts are mapped to.  
  
## See Also  
 [Host Initiated SSO](../core/host-initiated-sso.md)