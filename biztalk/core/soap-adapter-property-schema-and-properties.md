---
description: "Learn more about: SOAP Adapter Property Schema and Properties"
title: "SOAP Adapter Property Schema and Properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
