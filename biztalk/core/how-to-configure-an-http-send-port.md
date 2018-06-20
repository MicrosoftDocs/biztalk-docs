---
title: "How to Configure an HTTP Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send ports, HTTP adapters"
  - "HTTP adapters, send ports"
  - "configuring [HTTP adapters], send ports"
ms.assetid: 29c6868c-4570-4375-9494-08c07220eeb3
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure an HTTP Send Port
You can configure an HTTP send port either programmatically or by using the BizTalk Server Administration console.  
  
## Configure an HTTP send port programmatically
  
 The HTTP adapter stores its configuration information in the BizTalk Management database (also known as the Configuration database). You store configuration information in a custom XML property bag. During initialization of the HTTP adapter and during its run time, the server passes the configuration to the adapter as follows:  
  
- For the HTTP send handler, configuration information passes to the adapter by calling the **Load** method of the **IPersistPropertyBag** interface.  
  
- For the HTTP send ports, configuration information passes to the adapter as a set of properties on a message context. The HTTP namespace groups these properties together.  
  
  The BizTalk Explorer object model exposes the `ItransportInfo` adapter configuration interface for send ports, which contains the `TransportTypeData` read/write property. This property accepts the HTTP send port configuration property bag as a name/value pair XML string. Note that to set this property in the BizTalk Explorer object model, it must first be set on the `Address` property of the **ITransportInfo** interface.  
  
  Setting the **TransportTypeData** property of the **ITransportInfo** interface is not required. If it is not set, the HTTP adapter will use the default values for the HTTP send handler.  
  
  If send port configuration properties that duplicate the configuration for the handler are not defined, configuration properties for the handler are used. If the HTTP send handler does not have configuration values, the HTTP send adapter logs an error in the event log and moves the message to the backup adapter.  
  
  You can set configuration properties programmatically on a message context. You can set these properties in a BizTalk Server orchestration schedule or in custom pipeline components. The following rules apply when using these properties:  
  
- If the configuration property is set on an orchestration or in a custom pipeline component in a receive pipeline, then:  
  
  -   If a message is sent to a static send port, the property value will be overwritten with the value configured for that send port.  
  
  -   If a message is sent to a dynamic send port, the property value will not be overwritten.  
  
- If the configuration property is set in a custom pipeline component in a send pipeline, then:  
  
  -   The value will not be overwritten regardless of whether the message is sent to a static or dynamic send port.  
  
  The following table lists the configuration properties that you can set in the BizTalk Explorer object model for the HTTP send location.  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|**RequestTimeout**|xs:int|Time-out period of waiting for a response from the server. If set to zero (0), the system calculates the time-out based on the request message size.|**Minimum value:** 0<br /><br /> **Maximum value:** MAX_LONG|**Default value:** 0|  
|**ContentType**|xs:string|Content type of the request messages|**Minimum length:** 0<br /><br /> **Maximum length:** 256|**Default value:** Text/XML|  
|**MaxRedirects**|xs:int|Maximum number of times that the HTTP adapter can redirect the request.|**Minimum value:** 0<br /><br /> **Maximum value:** 10|**Default value:** 5|  
|**UseHandlerProxySettings**|xs:boolean|Specifies whether the HTTP send port will use the proxy configuration for the send handler.|None|**Default value:** True<br /><br /> When true, the send port will use the proxy settings specified at the handler level. When false, the send adapter will use the proxy information specified on the send port.|  
|**UseProxy**|xs:boolean|Specifies whether the HTTP adapter will use the proxy server. The proxy server can be shared by all HTTP send ports.|None|**Default value:** False<br /><br /> This property is ignored if **UseHandlerProxySettings** is **True**.|  
|**ProxyName**|xs:string|Specifies the proxy server name.|**Minimum length:** 0<br /><br /> **Maximum length:** 256|**Default value:** Empty<br /><br /> The HTTP send adapter ignores this property if the **UseHandlerProxySettings** property is set to **True**. Otherwise, the HTTP send adapter uses this property only if **UseProxy** is **True**. This property is required if **UseProxy** is **True**.|  
|**ProxyPort**|xs:int|Specifies the proxy server port.|**Minimum value:** 0<br /><br /> **Maximum value:** 65535|**Default value:** 80<br /><br /> The HTTP send adapter ignores this property if **UseHandlerProxySettings** is **True**. Otherwise, HTTP send adapter uses this property only if **UseProxy** is **True**. This property is required if **UseProxy** is **True**.|  
|**ProxyUsername**|xs:string|Specifies the user name for authentication with the proxy server.|**Minimum length:** 0<br /><br /> **Maximum length:** 256|**Default value:** empty<br /><br /> The HTTP send adapter ignores this property if **UseHandlerProxySettings** is **True**. Otherwise, HTTP send adapter uses this property only if **UseProxy** is **True**.|  
|**ProxyPassword**|xs:string|Specifies the user password for authentication with the proxy server.|**Minimum length:** 0<br /><br /> **Maximum length:** 256|**Default value:** empty<br /><br /> The HTTP send adapter ignores this property if **UseHandlerProxySettings** is **True**. Otherwise, HTTP send adapter uses this property only if **UseProxy** is **True**.|  
|**AuthenticationScheme**|xs:string|Type of authentication to use with the destination server.|None|**Valid values:**<br /><br /> -   **Anonymous (Default)**<br />-   **Basic**<br />-   **Digest**<br />-   **Kerberos**|  
|**Username**|xs:string|User name to use for authentication with the server.|**Minimum length:** 0<br /><br /> **Maximum length:** 256|**Default value:** Empty<br /><br /> This value is required if you select **Basic** or **Digest** authentication. The HTTP adapter ignores the value of this property if **UseSSO** is **True**.|  
|**Password**|xs:string|User password to use for authentication with the server.|**Minimum length:** 0<br /><br /> **Maximum length:** 256|**Default value:** empty<br /><br /> This value is required if you select **Basic** or **Digest** authentication. The value of this property is ignored if **UseSSO** is **True**.|  
|**EnableChunkedEncoding**|xs:boolean|Specifies whether or not chunked encoding is used by the HTTP adapter|None|**Default value:**<br /><br /> True|  
|**Certificate**|xs:string|Thumbprint of the client SSL certificate.|**Minimum length:** 0<br /><br /> **Maximum length:** 59|**Default value:** Empty|  
|**UseSSO**|xs:boolean|Specifies if SSO will be used for the send port.|None|**Default value:** False|  
|**AffiliateApplicationName**|xs:string|Name of the affiliate application to use for SSO.|**Minimum length:** 0<br /><br /> **Maximum length:** 256|**Default value:** empty<br /><br /> Required if **UseSSO** is **True**.|  
  
 The following code shows the XML string to use to set these properties:  
  
```  
<CustomProps>  
   <ContentType vt="8">text/xml</ContentType>  
   <RequestTimeout vt="3">0</RequestTimeout>  
   <MaxRedirects vt="3">5</MaxRedirects>  
   <UseHandlerProxySettings vt="8">-1</UseHandlerProxySettings>  
   <UseProxy vt="8">-1</UseProxy>  
   <ProxyName vt="8">sdfsd</ProxyName>  
   <ProxyPort vt="3">80</ProxyPort>  
   <ProxyUsername vt="8">Somename</ProxyUsername>  
   <ProxyPassword vt="8">Somepassword</ProxyPassword>  
   <AuthenticationScheme vt="8">Basic</AuthenticationScheme>  
   <Username vt="8">Somename</Username>  
   <Password vt="8">Somepassword</Password>  
   <EnableChunkedEncoding vt="11">1</EnableChunkedEncoding>  
   <Certificate vt="8">AAAA BBBB CCCC DDDD</Certificate>  
   <UseSSO vt="11">0</UseSSO>  
   <AffiliateApplicationName vt="8">Name</AffiliateApplicationName>  
</CustomProps>  
```  
  
## Configure an HTTP send port with the BizTalk Server Administration console
  
 You can set HTTP send port adapter variables in the BizTalk Server Administration console. If properties are not set for the send port, the default send handler values set in the BizTalk Server Administration console are used.  
  
> [!NOTE]
>  The configuration properties described in this topic are common for both one-way and request-response HTTP send ports.  
  
1.  In the BizTalk Server Administration console, create a new send port or double-click an existing send port to modify it. See [How to Create a Send Port](../core/how-to-create-a-send-port2.md) for more information. Configure all of the send port options and specify **HTTP** for the **Type** option in the **Transport** section on the **General** tab.  
  
2.  On the **General** tab, in the **Transport** section, click the **Configure** button next to **Type**.  
  
3.  In the **HTTP Transport Properties** dialog box, on the **General** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Destination URL**|Required. Specify the address to send HTTP requests. Include query strings appended to the base URL.<br /><br /> **Type:** String<br /><br /> **Maximum length:** 256<br /><br /> For more information, see [Restrictions on the Destination URL Property](../core/restrictions-on-the-destination-url-property.md). **Note:**  The URI for a send port or receive location cannot exceed 256 characters.|  
    |**Enable chunked encoding**|Specify to use chunked encoding. If this option is enabled, the HTTP adapter will use HTTP chunked encoding with maximum chunk size of 8 KB. Chunked encoding is implicitly disabled if the HTTP send handler is configured to **Use proxy**.<br /><br /> **Type:** Boolean<br /><br /> **Default Value:** True|  
    |**Request timeout (sec)**|Specify the time-out in seconds for the HTTP/HTTPS transmission. If the HTTP adapter does not receive the response within this time, the service logs the error and resubmits the message based on the retry infrastructure.<br /><br /> If set to zero (0), the BizTalk Messaging Engine calculates the time-out based on the request message size. If you do not provide a value, the value for the handler is used.<br /><br /> **Type:** Long<br /><br /> **Minimum value:** 0<br /><br /> **Maximum value:** MAX_LONG|  
    |**Maximum redirects**|Specify the maximum redirects allowed for the message being sent.<br /><br /> **Default value:** 5<br /><br /> **Type:** Int<br /><br /> **Minimum value:** 0<br /><br /> **Maximum value:** 10|  
    |**Content type**|Specify the content type of the request messages.<br /><br /> If this value is not set, the value for the handler is used.<br /><br /> **Type:** String<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 256|  
  
4.  In the **HTTP Transport Properties** dialog box, on the **Proxy (Handler override)** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Use Handler's default proxy configuration**|Specify that the send port configuration must use the proxy settings specified for the HTTP send handler.<br /><br /> This is the default setting.|  
    |**Do not use proxy**|Specify whether the HTTP send handler uses the proxy server.<br /><br /> If selected, the HTTP send handler for this send port does not use the proxy server.|  
    |**Use proxy**|Specify whether the HTTP send handler uses the proxy server.<br /><br /> If selected, the HTTP send handler uses the proxy server.|  
    |**Server**|Specify the proxy server address for this send port.<br /><br /> This property only requires a value if **Use proxy** is selected.<br /><br /> **Type:** String<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 256|  
    |**Port**|Specify the proxy server port for this send port.<br /><br /> This property only requires a value if **Use proxy** is selected.<br /><br /> **Default Value:** 80<br /><br /> **Type:** Long<br /><br /> **Minimum value:** 0<br /><br /> **Maximum value:** 65535|  
    |**User name**|Specify the user name for authentication with the proxy server.<br /><br /> This property only requires a value if **Use proxy** is selected.<br /><br /> **Type:** String<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 256|  
    |**Password**|Specify the user password for authentication with the proxy server.<br /><br /> This property only requires a value if **Use proxy** is selected.<br /><br /> **Type:** String<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 256|  
  
5.  In the **HTTP Transport Properties** dialog box, on the **Authentication** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Authentication Type**|Specify the type of authentication to use with the destination server.<br /><br /> Valid options are:<br /><br /> -   **Anonymous**<br />-   **Basic**<br />-   **Digest**<br />-   **Kerberos**<br /><br /> **Default Value:** Anonymous|  
    |**Credentials**|Specify the type of credentials to use.<br /><br /> Only available if the **Authentication Type** is **Basic** or **Digest**.<br /><br /> Valid options are:<br /><br /> -   **Do Not Use Single Sign-On**<br />     **User name:**<br />     The user name to use for authentication with the destination server. If the **Authentication Type** property is **Anonymous** or **Kerberos**, this option is disabled. This property requires a value if **Basic** or **Digest** is selected, and Enterprise Single Sign-On is not used.<br />     **Minimum length:** 0<br />     **Maximum length:** 256<br />     **Password:**<br />     The password to use for authentication with the destination server. If the **Authentication Type** property is **Anonymous** or **Kerberos**, this option is disabled. This property requires a value if **Basic** or **Digest** is selected, and Single Sign-On is not used.<br />     **Minimum length:** 0<br />     **Maximum length:** 256<br />-   **Use Single Sign-On**<br />     Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.<br />     **Affiliate Application**<br />     Specifies the affiliate application to use for Single Sign-On.<br />     Choose the applications that you want to include in Single Sign-On.<br />     **Minimum length:** 0<br />     **Maximum length:** 256|  
    |**SSL client certificate thumbprint**|Specify the thumbprint of the client certificate to use for establishing a Secure Sockets Layer (SSL) connection.<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 59|  
  
6.  Click **OK** and **OK** again to save settings.  
  
## See Also  
 [Configuring an HTTP Send Port](../core/configuring-an-http-send-port.md)