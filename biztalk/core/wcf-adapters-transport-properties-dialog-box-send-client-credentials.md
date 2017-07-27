---
title: "WCF Adapters Transport Properties Dialog Box, Send, Client Credentials | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-adapters.transport.send.clientcredentials"
helpviewer_keywords: 
  - "properties, WCF adapters"
  - "WCF adapters, client credentials"
  - "WCF adapters, properties"
  - "client credentials"
ms.assetid: 37d87be9-3664-4bab-a781-21dd8ad13337
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Adapters Transport Properties Dialog Box, Send, Client Credentials
Use the **Client Credentials** dialog box to specify the credentials to be used when sending messages.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Do not use Single Sign-On**|Use the **User name** and **Password** properties to set client credentials for authentication with the destination server.<br /><br /> This is the default setting.|  
|**User name**|Specify the user name to use for authentication with the destination server when the **Do not use Single Sign-On** option is selected. You do not have to use the domain\user format for this property.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**Password**|Specify the password to use for authentication with the destination server when the **Do not use Single Sign-On** option is selected.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**Use Single Sign-On**|Use Single Sign-On to retrieve client credentials for authentication with the destination server. **Note:**  For a WCF send port to validate and redeem an SSO ticket properly, the **SSOTicket** and **OriginatorSID** context properties must be available in a message to be sent. A receive location with Single Sign-On enabled can promote these properties from a sender's Windows account. <br /><br /> The default value is cleared.|  
|**Affiliated application**|Specify the affiliate application to use for Single Sign-On. For information about populating this list, see the appropriate topics in See Also.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default value is cleared.|  
  
## See Also  
 [Using SSO](../core/using-sso.md)   
 [How to Configure a WCF-BasicHttp Send Port](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f)   
 [How to Configure a WCF-WSHttp Send Port](../core/how-to-configure-a-wcf-wshttp-send-port.md)   
 [How to Configure a WCF-NetTcp Send Port](../core/how-to-configure-a-wcf-nettcp-send-port.md)   
 [How to Configure a WCF-NetMsmq Send Port](../core/how-to-configure-a-wcf-netmsmq-send-port.md)   
 [How to Configure a WCF-NetNamedPipe Send Port](../core/how-to-configure-a-wcf-netnamedpipe-send-port.md)