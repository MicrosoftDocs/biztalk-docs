---
title: "Security Tab for TCP-IP (Remote Environment Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/19/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15242"
ms.assetid: 583f1cab-b957-408d-b3af-c03af2088820
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Security Tab for TCP/IP (Remote Environment Properties)
Use the **Security** tab to set the security properties of the remote environment for TCP/IP.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Enable Single Sign-on**|Select this option to require that the TI run-time environment uses Single Sign-on (SSO). Clear this option to allow TI to communicate with the mainframe region without setting user ID and password information.|  
|**Affiliate application**|Select the SSO affiliate application to be queried for credentials. The list displays all the affiliate applications defined in the SSO. The display name of the affiliate application is a concatenation of the affiliate application name and description, separated by a hyphen.|  
|**Allow application to override selected authentication**|Select this option to enable the TI run-time environment to use the application override mechanism for obtaining user ID and password information. The client application must be written to support the TI security override mechanism. Clear this option to base the user ID and password solely on previously selected user credentials. This security option can be applied to a TI object deployed in an ASP.NET application. **Note:**  This option appears only if **Enable Single Sign-on** is selected.|  
|**Require client provided security**|Select this option to require the client to provide the security credentials, either by using the client context or by making call-back security available. **Note:**  This option appears only if **Enable Single Sign-on** is cleared.|  
  
> [!CAUTION]
>  The properties of a remote environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the remote environment to function incorrectly.  
  
## See Also  
 [Remote Environments Node](../core/remote-environments-node.md)   
 [Remote Environment Node](../core/remote-environment-node.md)   
 [TI Manager Properties](../core/ti-manager-properties.md)