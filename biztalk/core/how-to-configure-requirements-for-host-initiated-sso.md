---
title: "How to Configure Requirements for Host Initiated SSO | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service accounts, granting privileges [SSO]"
  - "host initiated SSO, configuring"
  - "domain function level [SSO]"
  - "host initiated SSO, Transaction Integrator (TI)"
  - "SPN [SSO]"
  - "managing [SSO], granting TCB privileges"
  - "Transaction Integrator (TI)"
  - "host initiated SSO, SPN"
  - "host initiated SSO, TCB privileges"
  - "configuring, host initiated SSO"
  - "creating, SPNs [SSO]"
  - "TCB privileges [SSO]"
  - "managing [SSO], host initiated"
  - "host initiated SSO, domain function level"
  - "service accounts, SSO"
  - "SSO, host initiated"
  - "managing [SSO], creating SPNs"
  - "SSO, service accounts"
ms.assetid: 91d77c9f-bab2-4f6e-8bce-e31c59cebb20
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Requirements for Host Initiated SSO
Although Enterprise SSO and host initiated SSO have certain aspects in common, certain platform and Active Directory requirements are unique to host initiated SSO. This topic discusses those requirements, and lists the steps to check or create them on your system.  
  
- Host initiated SSO can be executed only on a native Windows Server 2008 domain environment.  
  
- The service account for SSO Service that is performing host initiated SSO must be configured to have TCB privileges. (You can configure this for the service account in the domain security policy.)  
  
  In addition, certain requirements are necessary when using Transaction Integrator for Host Initiated Processing. TI for HIP leverages host initiated SSO to achieve Single Sign-On for non-Windows users.  
  
  For example, service account for TI for HIP service runs under a service account domainname\hipsvc. This service can host applications that want to access remote or local resources on Windows with the Windows account that correspond to the non-Windows account.  
  
  The domainname\hipsvc account must belong to the Application Administrator group account for the Affiliate Application that is being used for Single Sign-On.  
  
  The domainname\hipsvc account must have constrained delegation privileges to use host initiated Single Sign-On. This can be configured by the domain administrator in Active Directory. Delegation can be configured for accounts that have registered SPNs. Constrained delegation allows the service account to access only components that are specified by the administrator.  
  
### To check your domain function level  
  
1.  In your **Active Directory Domains and Trusts** MMC snap-in, right click the node **Active Directory Domains and Trusts**, and then click **Raise Forest Functional Level**.  
  
2.  Verify that the functional level is **Windows Server 2008**. If it is not, refer to your Active Directory documentation before you attempt to change the setting.  
  
### To create an SPN  
  
1. Download the **setspn** utility from the following location: [http://go.microsoft.com/fwlink/?LinkId=33178](http://go.microsoft.com/fwlink/?LinkId=33178).  
  
2. On the **Start** menu, click **Run**.  
  
3. In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
4. At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
5. Type **setpsn -a hipsvc\computername.domain.com domain\hissvc**  
  
    where **hipsvc\computername.domain.com** is the service that will perform the operation and the computer it is running on, and **domain\hissvc** is the service account for hipsvc.  
  
   After doing this, you can configure constrained delegation in Active Directory for this service account (domain\hissvc) to access the appropriate resource in the network.  
  
#### To give TCB privileges for the SSO service account  
  
-   Under your **Domain Security Policy - Local Policies - User Rights Assignment**, add the SSO Service account to the **Act as part of operating system** policy.  
  
     For more information about Kerberos Protocol Transition and Constrained Delegation, go to [http://go.microsoft.com/fwlink/?LinkId=195484](http://go.microsoft.com/fwlink/?LinkId=195484).  
  
## See Also  
 [Host Initiated SSO](../core/host-initiated-sso.md)