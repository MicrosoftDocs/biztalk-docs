---
title: "Configure a New Security Policy Wizard Page (in the New Security Policy Wizard) (2)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15369"
ms.assetid: e52c0ef7-7215-4726-ae80-cc1472029e6a
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Configure a New Security Policy Wizard Page (in the New Security Policy Wizard) (2)
Use the second **Configure a New Security Policy** wizard page to identify the source of the host user ID and password and determine how they are translated into Windows-based credentials. This wizard page appears only if **Host-initiated Single Sign-on** is selected on the **Configure a new security policy** wizard page.  
  
 Select the source of the credentials and the default user, and then select the credential mapping.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Security policy**|View the name of the security policy.|  
|**Affiliate application**|Select the Single Sign-On affiliate application that manages the translation of host user ID and password credentials to Windows credentials.|  
|**Single Sign-on mapping use**|Specify the credentials to be used when mapping to Single Sign-On.|  
|**Default credentials**|Select to enter the user ID and password used if the request from the host does not contain a user ID and password or the user ID and password are set to spaces or nulls. When selected, enables the **SSO affiliate application** and **User** boxes. **Note:**  This option is disabled if **Use HIP application credentials** is selected on the General tab.|  
|**Group application**|Select the|  
|**User**|Type the user name or select a previously entered host user name to be used in the lookup call to SSO.|  
  
## See Also  
 [Completing the Security Policy Wizard Page](../core/completing-the-security-policy-wizard-page.md)   
 [New Security Policy Wizard](../core/new-security-policy-wizard.md)