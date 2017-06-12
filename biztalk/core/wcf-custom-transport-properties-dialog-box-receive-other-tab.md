---
title: "WCF-Custom Transport Properties Dialog Box, Receive, Other Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-custom.transport.receive.other"
helpviewer_keywords: 
  - "credentials, WCF-Custom adapters"
  - "WCF-Custom adapters, properties"
  - "properties, WCF-Custom adapters"
  - "WCF-Custom adapters, credentials"
ms.assetid: f28cf430-400a-4ce0-8378-f2c0f98b41f4
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-Custom Transport Properties Dialog Box, Receive, Other Tab
Use the **Other** tab to specify the following:  
  
-   The credentials for this receive location to use when polling an external service  
  
-   Whether this receive location issues an SSO ticket  
  
-   Whether this receive location preserves message order when processing messages  
  
 You can create a custom channel to poll an external service to retrieve response messages from the service like the SQL receive adapter and the FTP receive adapter do. If you configure the custom binding to use this custom channel, the receive location uses the specified credentials when sending solicit messages to an external service.  
  
> [!NOTE]
>  For this receive location to use the credentials specified on the **Other** tab, you must use the **ClientCredentials** object that BizTalk Server passes along when implementing the custom channel and binding.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Credentials - None**|Do not use any credentials when this receive location sends solicit messages to poll an external service, or this receive location does not need to poll any external service.<br /><br /> This is the default setting.|  
|**Credentials - User account**|Use the credentials specified in the **Username** and **Password** properties when this receive location sends solicit messages to poll an external service.<br /><br /> The default value is cleared.|  
|**Credentials - User name**|Specify the user name for this receive location to use when polling an external service to retrieve response messages. This property is required when the **User account** option is selected.<br /><br /> The default value is cleared.|  
|**Credentials - Password**|Specify the password for this receive location to use when polling an external service to retrieve response messages. This property is required when the **User account** option is selected.<br /><br /> The default value is cleared.|  
|**Credentials - Get credentials from affiliate application**|Use the SSO affiliate application specified in the **Affiliate application** property when this receive location sends solicit messages to poll an external service.<br /><br /> The default value is cleared.|  
|**Credentials - Affiliate application**|Specify the SSO affiliate application to return external credentials to be used when this receive location sends solicit messages to poll an external service. The specified SSO affiliate application must have a mapping between the Windows account under which this receive location runs and the account for the external service. This property is required when the **Get credentials from affiliate application** option is selected.<br /><br /> The default value is cleared.|  
|**Credentials - Issue Single Sign-On ticket**|Use Single Sign-On to retrieve client credentials to issue an SSO ticket.  This option requires using the security mode that allows this receive location to impersonate the user account to issue an SSO ticket.<br /><br /> The default value is cleared.|  
|**Message order - Ordered processing**|Preserve message order when processing messages (for use with the NetMsmq binding).<br /><br /> The default value is cleared.|  
  
## See Also  
 [How to Configure a WCF-Custom Receive Location](../core/how-to-configure-a-wcf-custom-receive-location.md)   
 [How to Configure a WCF-CustomIsolated Receive Location](../core/how-to-configure-a-wcf-customisolated-receive-location.md)