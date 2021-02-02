---
description: "Learn more about: SOAP Adapter Property Schema and Properties"
title: "SOAP Adapter Property Schema and Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ProxyUsername property [SOAP adapters]"
  - "ClientConnectionTimeout property [SOAP adapters]"
  - "SOAP adapters, properties"
  - "ProxyAddress property [SOAP adapters]"
  - "UserDefined property [SOAP adapters]"
  - "AssemblyName property [SOAP adapters]"
  - "ClientCertificate property [SOAP adapters]"
  - "AffiliateApplicationName property [SOAP adapters]"
  - "schemas, SOAP adapters"
  - "AuthenticationScheme property [SOAP adapters]"
  - "UserName property, SOAP adapters"
  - "UseProxy property [SOAP adapters]"
  - "Password property [SOAP adapters]"
  - "configuring [SOAP adapters], schemas"
  - "UnknownHeaders property [SOAP adapters]"
  - "configuring [SOAP adapters], properties"
  - "UseSoap12 property [SOAP adapters]"
  - "UseHandlerSetting property [SOAP adapters]"
  - "SOAP adapters, schemas"
  - "ProxyPassword property [SOAP adapters]"
  - "UseSSO property [SOAP adapters]"
  - "MethodName property [SOAP adapters]"
  - "ProxyPort property [SOAP adapters]"
ms.assetid: b471cf4b-2d87-4aa2-ae4a-f48517fd4c94
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SOAP Adapter Property Schema and Properties
The following table lists the properties in the SOAP adapter property schema.  
  
 **Namespace:** `http://schemas.microsoft.com/BizTalk/2003/soap-properties`  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|**AssemblyName**|xs:string|Identifies the .NET type and assembly to be loaded and executed.|  
|**MethodName**|xs:string|Identifies the target method on the .NET assembly that is to be invoked.|  
|**Username**|xs:string|User name to use for authentication with the server.|  
|**Password**|xs:string|User password to use for authentication with the server.|  
|**ClientCertificate**|xs:string|Thumbprint of the client SSL certificate.|  
|**UseProxy**|xs:Boolean|Specifies whether the SOAP adapter uses a proxy server.|  
|**ProxyAddress**|xs:string|Specifies the proxy server address.|  
|**ProxyPort**|xs:int|Specifies the proxy server port.|  
|**ProxyUsername**|xs:string|Specifies the user name for authentication with the proxy server.|  
|**ProxyPassword**|xs:string|Specifies the user password for authentication with the proxy server.|  
|**UnknownHeaders**|xs:string|Specifies the serialized list of unknown SOAP headers.|  
|**AffiliateApplicationName**|xs:string|Defines the name of the affiliate application to use for SSO.|  
|**AuthenticationScheme**|xs:string|Specifies the type of authentication to use with the destination server.|  
|**UseSSO**|xs:boolean|Specifies whether the SOAP adapter uses SSO for the send port.|  
|**UseHandlerSetting**|xs:boolean|Specifies whether the SOAP send port uses the proxy configuration for the handler.|  
|**ClientConnectionTimeout**|xs:int|Specifies the time-out period of waiting for a response from the server. If set to zero (0), the system will calculate the time-out based on the request message size.|  
|**UserDefined**|xs:string|Defines user-defined classes.|  
|**UseSoap12**|xs:boolean|Specifies whether to generate proxy code that supports the SOAP 1.2 protocol.|  
  
## See Also  
 [Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md)
