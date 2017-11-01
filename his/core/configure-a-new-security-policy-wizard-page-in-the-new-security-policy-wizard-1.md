---
title: "Configure a New Security Policy Wizard Page (in the New Security Policy Wizard) (1)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15368"
ms.assetid: 7da59f96-abab-4785-b9c3-8bf456e296d7
caps.latest.revision: 3
robots: noindex,nofollow
---
# Configure a New Security Policy Wizard Page (in the New Security Policy Wizard) (1)
Use the first **Configure a New Security Policy** wizard page to identify the security policy and the source of the credentials. Type the name of the security policy, and then select the source for the credentials.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Security policy**|Type the name for the security policy. The name can be a maximum of 259 Unicode characters (alphabetic, numeric, space, and special). The name cannot be the same as that of an existing security policy. The name for the new security policy is a required field; you will receive an error message if you click **Next** without providing a name. The name is used to associate the security policy with an object view in other wizard pages and dialog boxes.|  
|**Credentials source used to invoke the server**|Specify the type or source of credentials that host-initiated processing will associate with the thread when the method on the server object is invoked.|  
|**Host-initiated Single Sign-on**|Select this option to use host user ID and password. This option is automatically selected if Single Sign-On (SSO) is not installed or not available.|  
|**Windows credentials of the HIP application**|Select this option to use Windows credentials that are specified on the HIP NT application service. This option is automatically disabled if Single Sign-On (SSO) is not installed or not available.|  
  
## See Also  
 [Configure a New Security Policy Wizard Page (in the New Security Policy Wizard) (2)](../core/configure-a-new-security-policy-wizard-page-in-the-new-security-policy-wizard-2.md)   
 [New Security Policy Wizard](../core/new-security-policy-wizard.md)