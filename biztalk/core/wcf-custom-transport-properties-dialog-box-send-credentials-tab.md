---
title: "WCF-Custom Transport Properties Dialog Box, Send, Credentials Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-custom.transport.send.clientcredentials"
helpviewer_keywords: 
  - "credentials, WCF-Custom adapters"
  - "WCF-Custom adapters, properties"
  - "properties, WCF-Custom adapters"
  - "WCF-Custom adapters, credentials"
ms.assetid: 8bde7371-7635-407f-ac56-74631e15c811
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-Custom Transport Properties Dialog Box, Send, Credentials Tab
Use the **Credentials** tab to specify the credentials to be used when sending messages.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Do not use Single Sign-On**|Use the **User name** and **Password** properties to set client credentials for authentication with the destination server.<br /><br /> This is the default setting.|  
|**User name**|Specify the user name to use for authentication with the destination server when the **Do not use Single Sign-On** option is selected.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**Password**|Specify the password to use for authentication with the destination server when the **Do not use Single Sign-On** option is selected.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**Use Single Sign-On**|Use Single Sign-On to retrieve client credentials for authentication with the destination server. **Note:**  For a WCF send port to validate and redeem an SSO ticket properly, the **SSOTicket** and **OriginatorSID** context properties must be available in a message to be sent. A receive location with Single Sign-On enabled can promote these properties from a sender's Windows account. <br /><br /> The default value is cleared.|  
|**Affiliated application**|Specify the affiliate application to use for Single Sign-On. For information about populating this list, see the appropriate topics in See Also.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default value is cleared.|  
|**Address**|Specify the address of the proxy server. Use the **https** or the **http** scheme depending on the security configuration. This address can be followed by a colon and the port number. For example, http://127.0.0.1:8080. This property requires a value only if you intend to configure the proxy settings.<br /><br /> Type: String<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**User name**|Specify the user name to use for authentication. If integrated authentication is used, the user name includes the domain, that is, domain\username. If Basic or Digest authentication is used, the user name does not include domain\\. This property requires a value only if you intend to configure the proxy settings.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**Password**|Specify the password to use for authentication.<br /><br /> This property requires a value only if you intend to configure the proxy settings.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
  
## See Also  
 [How to Configure a WCF-Custom Send Port](../core/how-to-configure-a-wcf-custom-send-port.md)   
 [Using SSO](../core/using-sso.md)