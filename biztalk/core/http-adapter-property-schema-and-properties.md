---
description: "Learn more about: HTTP Adapter Property Schema and Properties"
title: "HTTP Adapter Property Schema and Properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# HTTP Adapter Property Schema and Properties
The following table lists the properties in the HTTP adapter property schema.  
  
 **Namespace:** `http://schemas.microsoft.com/BizTalk/2003/http-properties`  
  
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
|**HttpCookie**|xs:string||  
|**AuthenticationScheme**|xs:string|Type of authentication to use with the destination server.|  
|**Certificate**|xs:string|Thumbprint of client SSL certificate.|  
|**UseSSO**|xs:boolean|Specifies whether the HTTP send port will use SSO.|  
|**AffiliateApplicationName**|xs:string|Name of affiliate application to use for SSO.|  
|**InboundHttpHeaders**|xs:string|Contains the HTTP headers from the inbound HTTP request.|  
|**SubmissionHandle**|xs:string|Contains the BizTalk Server correlation token (GUID) for the request message.|  
|**EnableChunkedEncoding**|xs:boolean|Specifies whether or not chunked encoding is used by the HTTP adapter.|  
|**UserHttpHeaders**|xs:string|Contains the customized headers contained in the HTTP request or response message<br /><br /> The value of the **UserHttpHeaders** property must have the following format:<br /><br /> `Header1: value\r\nHeader2: value\r\n`<br /><br /> **Note** Put a colon (:) and a SPACE character ( ) between the header and the value. An empty header will cause the entry to be filtered out. An empty value is okay.<br /><br /> You can modify the following five standard HTTP headers by using the **UserHttpHeaders** property:<br /><br /> - Accept<br /><br /> - Referrer<br /><br /> - Expect<br /><br /> - If-Modified-Since<br /><br /> - User-Agent|  
|**ResponseStatusCode**|xs:int|HTTP response status codes indicate whether a specific HTTP request has been successfully completed. Responses are grouped in five classes: <br/><br/>- Informational responses (100–199)<br/>- Successful responses (200–299)<br/>- Redirection messages (300–399)<br/>- Client error responses (400–499)<br/>- Server error responses (500–599) |

## See Also  
 [Configuring the HTTP Adapter](../core/configuring-the-http-adapter.md)
