---
description: "Learn more about: HTTP Adapter Configuration Properties"
title: "HTTP Adapter Configuration Properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# HTTP Adapter Configuration Properties
The following table lists the configuration properties that you can set for an HTTP adapter receive location:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|ReturnCorrelationHandle|VT_BOOL|Specify that if successful, the receive location sends the correlation token of the submitted message on the HTTP response to the client.|This property is valid only for one-way receive locations.<br /><br /> Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|None|  
|ResponseContentType|VT_BSTR|Specify the content type of HTTP response messages that the receive location sends back to clients.|This property is valid only for request-response receive locations.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|The default value is text/xml.|  
|SuspendFailedRequests|VT_BOOL|Specify whether or not to suspend HTTP requests that fail inbound processing.|Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|A value of 0 (false) indicates to discard the failed request and send an error status code (401 or 500) to the client.<br /><br /> A value of -1 (true) indicates to suspend the failed request and send an "Accepted" status code (200) to the client for one way receive ports or an "Error" status code (500) to the client for two way receive ports.<br /><br /> The default value is 0 (false).|  
|UseSSO|VT_BOOL|Specify that Enterprise Single Sign-On is used.|Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is 0 (false).|  
|LoopBack|VT_BOOL|Specify that the request message received on this location is routed either to a send port or back to this receive location to be sent as a response.|This property is valid only for request-response receive locations.<br /><br /> Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is 0 (false).|  
  
 The following code shows the format of the XML string you use to set the properties:  
  
```  
<CustomProps>  
<ReturnCorrelationHandle vt="11">-1</ReturnCorrelationHandle>  
<ResponseContentType vt="8">text/xml</ResponseContentType>  
<SuspendFailedRequests vt="11">-1</SuspendFailedRequests>  
<UseSSO vt="11">-1</UseSSO>  
<LoopBack vt="11">-1</LoopBack>  
</CustomProps></  
```  
  
 The following table lists the configuration properties that you can set for an HTTP adapter send port:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|ProxyPort|VT_I4|Specify the proxy server port for this send port.|Valid values are from 0 to 65535.|This property does not require a value if UseProxy is set to 0 (false).<br /><br /> The default value is 80.|  
|RequestTimeout|VT_I4|Specify the time-out in seconds for the HTTP/HTTPS transmission.|Valid values are from 0 to MAX_LONG.|If the HTTP adapter does not receive the response within this time, the service logs the error and resubmits the message based on the retry infrastructure.<br /><br /> If set to 0, the BizTalk Messaging Engine calculates the time-out based on the request message size. If you do not provide a value, the value for the handler is used.|  
|Certificate|VT_BSTR|Specify the thumbprint of the client certificate to use for establishing a Secure Sockets Layer (SSL) connection.|Minimum length: 0<br /><br /> Maximum length: 59|The default value is empty.|  
|AuthenticationScheme|VT_BSTR|Specify the type of authentication to use with the destination server.|Valid values are:<br /><br /> -   Anonymous<br />-   Basic<br />-   Digest<br />-   Kerberos|The default value is Anonymous.|  
|Username|VT_BSTR|Specify the user name to use for authentication with the destination server.|This property requires a value if an AuthenticationScheme of Basic or Digest is used, and Enterprise Single Sign-On is not used.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|None|  
|EnableChunkedEncoding|VT_BOOL|Specify to use chunked encoding.|Chunked encoding is implicitly disabled if the HTTP send handler is configured to Use proxy.<br /><br /> Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|If this option is enabled, the HTTP adapter will use HTTP chunked encoding with maximum chunk size of 8Kb.<br /><br /> The default value is 0 (false).|  
|UseProxy|VT_BOOL|Specify whether the HTTP send handler uses a proxy server.|Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is 0 (false).|  
|ProxyName|VT_BSTR|Specify the proxy server address for this send port.|Minimum length: 0<br /><br /> Maximum length: 256|This property does not require a value if UseProxy is set to 0 (false).|  
|UseSSO|VT_BOOL|Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.|Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is 0 (false).|  
|Password|VT_NULL|Specify the password to use for authentication with the destination server.|This property requires a value if an AuthenticationScheme of Basic or Digest is used, and Enterprise Single Sign-On is not used.<br /><br /> This value is always set to null when exporting a binding file. This field must be manually populated with the password before importing the binding file into the target BizTalk Server configuration.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|Set the type for this property to VT_BSTR (vt="8") before importing the binding file if you provide a value for this field.|  
|MaxRedirects|VT_I4|Specify the maximum redirects allowed for the message being sent.|Valid values are from 0 to 10.|The default value is 5.|  
|ContentType|VT_BSTR|Specify the content type of the request messages.|Minimum length: 0<br /><br /> Maximum length: 256|If this value is not set, the value for the handler is used.|  
|ProxyPassword|VT_NULL|Specify the user password for authentication with the proxy server.|This value is always set to null when exporting a binding file. This field must be manually populated with the password before importing the binding file into the target BizTalk Server configuration.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|This property does not require a value if UseProxy is set to 0 (false).|  
|ProxyUsername|VT_BSTR|Specify the user name for authentication with the proxy server.|Minimum length: 0<br /><br /> Maximum length: 256|This property does not require a value if UseProxy is set to 0 (false).|  
|UseHandlerSetting|VT_BOOL|Specify that the send port configuration must use the proxy settings specified for the HTTP Send Handler.|Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is -1 (true).|  
  
 The following code shows the format of the XML string you use to set the properties:  
  
```  
<CustomProps>  
<ProxyPort vt="3">80</ProxyPort>  
<RequestTimeout vt="3">60</RequestTimeout>  
<Certificate vt="8">A7 6D F9 06 5E FC 97 66 75 59 B5 D6 67 0C 84 DC 64 F5 BF B9</Certificate>  
<AuthenticationScheme vt="8">Basic</AuthenticationScheme>  
<Username vt="8">authenticateduser</Username>  
<EnableChunkedEncoding vt="11">-1</EnableChunkedEncoding>  
<UseProxy vt="11">-1</UseProxy>  
<ProxyName vt="8">proxyserver</ProxyName>  
<UseSSO vt="11">0</UseSSO>  
<Password vt="1" />  
<MaxRedirects vt="3">5</MaxRedirects>  
<ContentType vt="8">text/xml</ContentType>  
<ProxyPassword vt="1" />  
<ProxyUsername vt="8">proxyuser</ProxyUsername>  
<UseHandlerSetting vt="11">0</UseHandlerSetting>  
</CustomProps>  
```
