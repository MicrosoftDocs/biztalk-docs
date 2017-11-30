---
title: "General Tab (Security Policy Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15372"
ms.assetid: c855e861-6331-4361-a95b-d1fc8c4c5a50
caps.latest.revision: 4
---
# General Tab (Security Policy Properties)
The **General** tab of the properties page of a security policy defines the name of the policy and the source of the security credentials.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Policy**|Type the name for the security policy. The name can be a maximum of 259 Unicode characters (alphabetic, numeric, space, and special). The name cannot be the same as the name of an existing security policy. The name for the new security policy is a required field; you will receive an error message if you click **Next** without providing a name. The name is used to associate the security policy with an object view in other wizard pages and dialog boxes.|  
|**Host-initiated Single Sign-on**|Select this option to use host user ID and password. This option is automatically disabled if Single Sign-On (SSO) is not installed or not available.|  
|**Windows credentials of the HIP application**|Select this option to use Windows user ID and password specified on the HIP NT application service. This option is automatically selected if Single Sign-On (SSO) is not installed or not available.|  
|**Comment**|Type additional information about the security policy. The comment can be a maximum of 259 Unicode characters.|  
  
> [!CAUTION]
>  The properties of a security policy are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the security policy to function incorrectly.  
  
## See Also  
 [Security Policies Node](../HIS2010/security-policies-node1.md)   
 [Security Policy Node](../HIS2010/security-policy-node2.md)   
 [TI Manager Properties](../HIS2010/ti-manager-properties1.md)