---
title: "HTTP Adapter Property Schema and Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "AffiliateApplicationName property [HTTP adapters]"
  - "Certificate property [HTTP adapters]"
  - "Password property [HTTP adapters]"
  - "HTTP adapters, properties"
  - "InboundHttpHeaders property [HTTP adapters]"
  - "UseHandlerProxySettings property [HTTP adapters]"
  - "configuring [HTTP adapters], properties"
  - "schemas, HTTP adapters"
  - "RequestTimeout property [HTTP adapters]"
  - "ProxyPassword property [HTTP adapters]"
  - "UseSSO property [HTTP adapters]"
  - "HTTP adapters, schemas"
  - "AuthenticationScheme property [HTTP adapters]"
  - "ProxyName property [HTTP adapters]"
  - "ProxyPort property [HTTP adapters]"
  - "UseProxy property [HTTP adapters]"
  - "configuring [HTTP adapters], schemas"
  - "ContentType property [HTTP adapters]"
  - "MaxRedirects property [HTTP adapters]"
  - "ProxyUsername property [HTTP adapters]"
  - "UserName property, HTTP adapters"
ms.assetid: c9b50a82-8cb1-4521-9cf3-5fd77a3531e1
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Adapter Property Schema and Properties
The following table lists the properties in the HTTP adapter property schema.  
  
 **Namespace:** http://schemas.microsoft.com/BizTalk/2003/http-properties  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|**ProxyName**|xs:string|Specifies the proxy server name.|  
|**ProxyPort**|xs:int|Specifies the proxy server port.|  
|**UseHandlerProxySettings**|xs:boolean|Specifies whether the HTTP send port uses the proxy configuration for the handler.|  
|**UseProxy**|xs:boolean|Specifies whether HTTP adapter uses the proxy server.|  
|**RequestTimeout**|xs:int|Time-out period of waiting for a response from the server. If this property is set to zero (0), the system calculates the time-out on the request message size.|  
|**Username**|xs:string|The user name to use for authentication with the server.|  
|**Password**|xs:string|The user password to use for authentication with the server.|  
|**ProxyUsername**|xs:string|Specifies the user name for authentication with the proxy server.|  
|**ProxyPassword**|xs:string|Specifies the user password for authentication with the proxy server.|  
|**MaxRedirects**|xs:int|The maximum number of times that the HTTP adapter will redirect the request.|  
|**ContentType**|xs:string|Content type of the request messages.|  
|**AuthenticationScheme**|xs:string|Type of authentication to use with the destination server.|  
|**Certificate**|xs:string|Thumbprint of client SSL certificate.|  
|**UseSSO**|xs:boolean|Specifies whether the HTTP send port will use SSO.|  
|**AffiliateApplicationName**|xs:string|Name of affiliate application to use for SSO.|  
|**InboundHttpHeaders**|xs:string|Contains the HTTP headers from the inbound HTTP request.|  
|**SubmissionHandle**|xs:string|Contains the BizTalk Server correlation token (GUID) for the request message.|  
|**EnableChunkedEncoding**|xs:boolean|Specifies whether or not chunked encoding is used by the HTTP adapter.|  
|**UserHttpHeaders**|xs:string|Contains the customized headers contained in the HTTP request or response message<br /><br /> The value of the **UserHttpHeaders** property must have the following format:<br /><br /> `Header1: value\r\nHeader2: value\r\n`<br /><br /> **Note** Put a colon (:) and a SPACE character ( ) between the header and the value. An empty header will cause the entry to be filtered out. An empty value is okay.<br /><br /> You can modify the following five standard HTTP headers by using the **UserHttpHeaders** property:<br /><br /> - Accept<br /><br /> - Referrer<br /><br /> - Expect<br /><br /> - If-Modified-Since<br /><br /> - User-Agent|  
  
## See Also  
 [Configuring the HTTP Adapter](../core/configuring-the-http-adapter.md)