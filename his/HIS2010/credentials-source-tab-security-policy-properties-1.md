---
title: "Credentials Source Tab (Security Policy Properties)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15373"
ms.assetid: d101bc58-8cfb-4215-9c4a-27c41f539a8d
caps.latest.revision: 4
---
# Credentials Source Tab (Security Policy Properties)
The **Credentials Source** tab of the properties page of a security policy defines the source of the host user ID and password and describes how they are translated into Windows-based credentials.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Security policy**|View the name of the security policy.|  
|**Affiliate application**|Select the SSO affiliate application to be queried to gain access to the Windows credentials needed to execute methods on the server object. The list displays all the affiliate applications defined in the SSO. The display name of the affiliate application is a concatenation of the affiliate application name and description, separated by a hyphen. The selected application will be added to the security policy. **Note:**  The dropdown list is disabled if SSO is not installed or is not available.|  
|**Single Sign-on mapping use**|Specify the credentials to be used when mapping to Single Sign-on.|  
|**Default credentials**|Select this option to enter the user ID and password used if the request from the host does not contain a user ID and password or the user ID and password are set to spaces or nulls. This option enables the **Group application** and **User** boxes.|  
|**Group application**|The default user group provides the default user ID and password.|  
|**User**|Type or select the host user name used in the lookup call to SSO. **Note:**  The dropdown list is disabled if SSO is not installed or is not available.|  
  
> [!CAUTION]
>  The properties of a security policy are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the security policy to function incorrectly.  
  
## See Also  
 [Security Policies Node](../HIS2010/security-policies-node1.md)   
 [Security Policy Node](../HIS2010/security-policy-node2.md)   
 [TI Manager Properties](../HIS2010/ti-manager-properties1.md)