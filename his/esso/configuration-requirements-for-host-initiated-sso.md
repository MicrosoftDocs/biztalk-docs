---
title: "Configuration Requirements for Host Initiated SSO | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0471ccc4-80b2-41b6-b32f-779d75fd06ad
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuration Requirements for Host Initiated SSO
Although Enterprise Single Sign-On (SSO) and host-initiated SSO have certain aspects in common, certain platform and Active Directory requirements are unique to host-initiated SSO. This topic discusses those requirements, and lists the steps to check or create them on your system.  
  
- Host-initiated SSO can be executed only on a native Windows Server domain environment.  
  
- The service account for SSO Service that is performing host-initiated SSO must be configured to have Trusted Computing Base (TCB) privileges. (You can configure this for the service account in the domain security policy.)  
  
  In addition, certain requirements are necessary when using Transaction Integrator for Host-Initiated Processing (TI for HIP). TI for HIP uses host-initiated SSO to achieve Single Sign-On for non-Windows users.  
  
  For example, a service account for TI for HIP service runs under a service account *domainname\hipsvc*. This service can host applications that want to access remote or local resources on Windows with the Windows account that corresponds to the non-Windows account.  
  
  The *domainname\hipsvc* account must belong to the Application Administrator group account for the affiliate application that is being used for Single Sign-On.  
  
  The *domainname\hipsvc* account must have constrained delegation privileges to use host-initiated Single Sign-On. This can be configured by the domain administrator in Active Directory. Delegation can be configured for accounts that have registered service principal names (SPN). Constrained delegation allows the service account to access only components that are specified by the administrator.  
  
### To check your domain function level  
  
1.  In the **Active Directory Domains and Trusts** Microsoft Management Console (MMC) snap-in, right-click the **Active Directory Domains and Trusts** node, and then click **Raise Forest Functional Level**.  
  
2.  Verify that the functional level is **Windows Server 2003**. If it is not, refer to your Active Directory documentation before you attempt to change the setting.  
  
### To create an SPN  
  
1.  Download the **setspn** utility from the following location: [http://go.microsoft.com/fwlink/?LinkId=148820](http://go.microsoft.com/fwlink/?LinkId=148820)  
  
2.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
3.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type `setpsn -a hipsvc\computername.domain.com domain\hissvc`  
  
     where *hipsvc\computername.domain.com* is the service that will perform the operation and the computer it is running on, and *domain\hissvc* is the service account for hipsvc.  
  
## After you do this, you can configure constrained delegation in Active Directory for this service account (domain\hissvc) to access the appropriate resource in the network.  
  
#### To give TCB privileges for the SSO service account  
  
-   Under **Domain Security Policy - Local Policies - User Rights Assignment**, add the SSO Service account to the **Act as part of operating system** policy.  
  
     For more information about Kerberos Protocol Transition and Constrained Delegation, visit [http://go.microsoft.com/fwlink/?LinkId=148816](http://go.microsoft.com/fwlink/?LinkId=148816).  
  
## See Also  
 [Host Initiated Single Sign-On](../esso/host-initiated-single-sign-on.md)