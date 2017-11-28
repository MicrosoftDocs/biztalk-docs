---
title: "WCF-WebHttp Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 67a353e7-1ba3-427a-8e99-c9b8d83061cb
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-WebHttp Adapter
[!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the **WCF-WebHttp** adapter to send messages to RESTful services. The **WCF-WebHttp** send adapter sends HTTP messages to a service from a BizTalk message. The receive location receives messages from a RESTful service. For GET and DELETE request, the adapter does not use any payload. For POST and PUT request, the adapter uses the BizTalk message body part to the HTTP content/payload.  

This topic shows you how to create the receive location and send port using BizTalk Administration.

## Create a receive location
  
> [!NOTE]
>  Before completing the following procedure, you must have already added a one-way receive port. See [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).  
  
1.  In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Applications**, and then expand the application under you want to create a receive location.  
  
2.  In the left pane, click the **Receive Ports** node and in the right pane, right-click the receive port with which you want to associate the new receive location, and then click **Properties**.  
  
3.  In the left pane of the **Receive Port Properties** dialog box, select **Receive Locations**, and in the right pane click **New** to create a new receive location.  
  
4.  In the **Receive Location Properties** dialog box, in the **Transport** section, select **WCF-WebHttp** from the **Type** drop-down list, and then click **Configure** to configure the transport properties for the receive location.  
  
5.  In the **General** tab, configure the endpoint address for the REST interface from where the message is received.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Address (URI)**|Required. Specify the URI on which [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can receive HTTP-based RESTful messages.|  
    |**Endpoint Identity**|Optional. Specify the endpoint identity. These settings enable the endpoint to authenticate this receive location. In the handshake process between the endpoint and the receive location, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br /><br /> The default is an empty string.|  
    |**HTTP Method and URL Mapping**|BTS Operation Mapping allows users to map incoming HTTP requests to BTS Operation in the message context, based on the incoming HTTP Method and the URL sub-path. The incoming HTTP Method and the URL sub-path are matched against a set of HTTP method and the URI Template. If a match is found, the adapter promotes the **BTS.Operation** property to the BizTalk Message Context with the value specified in the message.<br /><br /> You can specify HTTP method to URL mapping as a singular format or a multi-mapping format. The multi-mapping format resembles the following:<br /><br /> `<BtsHttpUrlMapping> <Operation Name = "DelCust" Method="DELETE" Url="/Customer/12345</BtsHttpUrlMapping>`<br /><br /> In the above snippet, notice that the customer ID is provided as a constant value, which is *12345*. However, there could be scenarios when the customer ID, or any other query variable, must be determined at runtime. To enable such scenarios, you must provide the variable component of the URL within curly brackets { }. For example, in the above snippet, if you specify the customer ID as a variable, it would look like:<br /><br /> `<BtsHttpUrlMapping> <Operation Name = "DelCust" Method="DELETE" Url="/Customer/{ID}</BtsHttpUrlMapping>`<br /><br /> In such a case, you must also specify where the value for the variable **ID** must be picked from at runtime. You specify that using **Variable Mapping**.<br /><br />**Note**<br /> Within the URL field, any special XML characters must be "escaped". This ensures that the special XML characters are processed, and preserved by the port. For example, the `&` special character must be escaped as `&amp;`. <br /><br />From:<br />`Url=”/Customer?{ID}& group=Location”`<br />To: <br />`Url=”/Customer?{ID}&amp;group=Location”`|  
    |**Variable Mapping**|If you specified variables for the HTTP Method URL Mapping, you must specify what the variable maps to at runtime. Click the **Edit** button to launch the **Variable Mapping** dialog box. Under the **Variable** column, the dialog box lists the variables that you defined for **HTTP Method and URL Mapping**. In the **Property Name** field you must specify the name of the property that provides the value to be associated to the variable. You must have already defined/promoted this property as part of your solution. You must also provide the namespace for the property in the **Property Namespace** field.|  
  
6.  In the **Binding** tab, configure the time-out and encoding-related properties.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Open timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
    |**Send timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a send operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**. If you use a request-response receive port, this value specifies a time span for the whole interaction to complete, even if the client returns a large message.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
    |**Close timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
    |**Maximum received message size (bytes)**|Specify the maximum size, in bytes, for a message including headers, which can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br /><br /> The WCF-WebHttp adapter leverages the [WebHttpBinding](http://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.aspx) class in the buffered transfer mode to communicate with an endpoint. For the buffered transport mode, the [WebHttpBinding.MaxBufferSize](http://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.maxbuffersize.aspx) property is always equal to the value of this property.<br /><br /> Default value: 65536<br /><br /> Maximum value: 2147483647|  
    |**Max concurrent calls**|Specify the number of concurrent calls to a single service instance. Calls in excess of the limit are queued. Setting this value to 0 is equivalent to setting it to **Int32.MaxValue**.<br /><br /> The default is 200.|  
  
7.  In the **Security** tab, define the security capabilities of the WCF-WebHttp receive location.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Security mode**|Specify the type of security that is used. Valid values include the following:<br /><br /> -                          **None**: Messages are not secured during transfer.<br /><br /> - **Transport**: Security is provided using the HTTPS transport. The SOAP messages are secured using HTTPS. To use this mode, you must set up Secure Sockets Layer (SSL) in Microsoft Internet Information Services (IIS).<br /><br /> - **TransportWithMessageCredential**: Integrity, confidentiality, and service authentication are provided by the HTTPS transport. To use this mode, you must set up Secure Sockets Layer (SSL) in Microsoft Internet Information Services (IIS).<br /><br /> The default is **Transport**.|  
    |**Transport client credential type**|Specify the type of credential to be used when performing the client authentication. Valid values include the following:<br /><br /> - **None**: No authentication occurs at the transport level.<br /><br /> - **Basic**: Basic authentication. In Basic authentication, user names and passwords are sent in plain text over the network. You must create the domain or local user accounts corresponding to the credentials.<br /><br /> - **Digest**: Digest authentication. This authentication method operates much like Basic authentication, except that passwords are sent across the network as a hash value for additional security. Digest authentication is available only on domains with domain controllers running Windows Server operating systems authentication. You must create the domain or local user accounts corresponding to client credentials.<br /><br /> -                          **Ntlm**: NTLM authentication. Clients can send the credentials without sending a password to this receive location. You must create the domain or local user accounts corresponding to client credentials.<br /><br /> -                          **Windows**: Windows integrated authentication. Windows Communication Foundation negotiates Kerberos or NTLM, preferring Kerberos if a domain is present. If you want to use Kerberos it is important to have the client identify the service with a service principal name (SPN). You must create the domain or local user accounts corresponding to client credentials.<br /><br /> - **Certificate**: Client authentication using the client certificate. The CA certificate chain for the client X.509 certificates must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the clients can be authenticated to this receive location.<br /><br /> **Note**The **Transport client credential type** property must match the authentication scheme of the IIS virtual directory hosting this receive location. For example, if the property is set to **Windows**, you also need to enable **Integrated Windows authentication** for the virtual directory that hosts it. Similarly if the property is set to **None**, you must allow anonymous access to the virtual directory that hosts this receive location.<br /><br /> The default is **Windows**.|  
    |**Service certificate -Thumbprint**|Specify the thumbprint of the X.509 certificate for this receive location that the clients use to authenticate the service. The thumbprint can be selected by navigating the **My** store in the **Current User** location with the **Browse** button.<br /><br /> **Note** You must install the service certificate into the **Current User** location of the user account for the receive handler hosting this receive location.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 40<br /><br /> The default is an empty string.|  

8. In the **Behavior** tab, specify different behaviors at the service-level, and the endpoint-level. These behaviors are based off .NET Framework classes.  
  
    | Use this|To do this|  
    |--------------|----------------|  
    | ServiceBehavior | Extend the functionality of your WCF service at the service-level. You can add extensions that do different things, such as define the security settings, enable debugging, implement throttling, and use other .NET classes.  <br/><br/> Right-select **ServiceBehavior**, and **Add Extension**. The list shows you the .NET classes that can be used.|
    | EndpointBehavior | Extend the funcionality of how requests are received at the endpoint-level. You can add extensions that do different things, such as receive HTTP requests from a browser-based ASP.NET AJAX client, specify a time interval on transactions, choose to receive messages synchronously or asynchronously, and use other .NET classes. <br/><br/> Right-select **EndpointBehavior**, and **Add Extension**. The list shows you the .NET classes that can be used.|

    This is similar to the behavior configuration for a WCF-Custom receive location. See the **WCF-Custom Transport Properties Dialog Box, Receive, Behavior** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
    
9.  In the **Messages** tab, specify the data selection for the SOAP **Body** element.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Outbound HTTP Headers**|Specifies the HTTP headers that are stamped on the response message, if any.|  
    |**Disable location on failure**|Specify whether to disable the receive location that fails inbound processing due to a receive pipeline failure or a routing failure.<br /><br /> The default is cleared.|  
    |**Suspend request message on failure**|Specify whether to suspend the request message that fails inbound processing due to a receive pipeline failure or a routing failure.<br /><br /> The default value is cleared.|  
    |**Include exception detail in faults**|Specify whether to return SOAP faults when an error occurs to easy debugging.<br /><br /> The default value is cleared.|  
  
9. Click **OK**.  
  
10. Enter the appropriate values in the **Receive Location Properties** dialog box to complete the configuration of the receive location and click **OK** to save settings. For information about the **Receive Locations Properties** dialog box, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  

## Create the send port

1.  In the BizTalk Administration console, create a new send port or double-click an existing send port to modify it. See [How to Create a Send Port](../core/how-to-create-a-send-port2.md). Configure all of the send port options and specify **WCF-WebHttp** for the **Type** option in the **Transport** section of the **General** tab.  
  
2.  On the **General** tab, in the **Transport** section, click the **Configure** button.  
  
3.  In the **General** tab, configure the endpoint address for the REST interface where the message is sent.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Address (URI)**|Required. Specify the URI for the REST interface where the message is sent.|  
    |**Endpoint Identity**|Optional. Specify the endpoint identity. These settings enable the endpoint to authenticate this send port. In the handshake process between the endpoint and the receive location, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br /><br /> The default is an empty string.|  
    |**HTTP Method and URL Mapping**|BTS Operation Mapping allows users to map incoming HTTP requests to BTS Operation in the message context, based on the incoming HTTP Method and the URL sub-path. The incoming HTTP Method and the URL sub-path are matched against a set of HTTP method and the URI Template. If a match is found, the adapter promotes the **BTS.Operation** property to the BizTalk Message Context with the value specified in the message.<br /><br /> You can specify HTTP method to URL mapping as a singular format or a multi-mapping format. The multi-mapping format resembles the following:<br /><br /> `BtsHttpUrlMapping> <Operation Name = "DelCust" Method="DELETE" Url="/Customer/12345" /> </BtsHttpUrlMapping>`<br /><br /> In the above snippet, notice that the customer ID is provided as a constant value, which is *12345*. However, there could be scenarios when the customer ID, or any other query variable, must be determined at runtime. To enable such scenarios, you must provide the variable component of the URL within curly brackets { }. For example, in the above snippet, if you specify the customer ID as a variable, it would look like:<br /><br /> `<BtsHttpUrlMapping> <Operation Name = "DelCust" Method="DELETE" Url="/Customer/{ID}" /> </BtsHttpUrlMapping>`<br /><br /> In such a case, you must also specify where the value for the variable **ID** must be picked from at runtime. You specify that using **Variable Mapping**. <br /><br />**Note**<br /> Within the URL field, any special XML characters must be "escaped". This ensures that the special XML characters are processed, and preserved by the port. For example, the `&` special character must be escaped as `&amp;`. <br /><br />From:<br />`Url=”/Customer?{ID}& group=Location”`<br />To: <br />`Url=”/Customer?{ID}&amp;group=Location”`|  
    |**Variable Mapping**|If you specified variables for the HTTP Method URL Mapping, you must specify what the variable maps to at runtime. Click the **Edit** button to launch the **Variable Mapping** dialog box. Under the **Variable** column, the dialog box lists the variables that you defined for **HTTP Method and URL Mapping**. In the **Property Name** field you must specify the name of the property that provides the value to be associated to the variable. You must have already defined/promoted this property as part of your solution. You must also provide the namespace for the property in the **Property Namespace** field.|  
  
4.  In the **Binding** tab, configure the time-out and encoding-related properties.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Open timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
    |**Send timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a send operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**. If you use a request-response receive port, this value specifies a time span for the whole interaction to complete, even if the client returns a large message.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
    |**Close timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
    |**Maximum received message size (bytes)**|Specify the maximum size, in bytes, for a message including headers, which can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br /><br /> The WCF-WebHttp adapter leverages the [WebHttpBinding](http://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.aspx) class in the buffered transfer mode to communicate with an endpoint. For the buffered transport mode, the [WebHttpBinding.MaxBufferSize](http://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.maxbuffersize.aspx) property is always equal to the value of this property.<br /><br /> Default value: 65536<br /><br /> Maximum value: 2147483647|  
  
5.  In the **Security** tab, define the security capabilities of the WCF-WebHttp send port.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Security mode**|Specify the type of security that is used. Valid values include the following:<br /><br /> -   **None**: Messages are not secured during transfer.<br />-   **Transport**: Security is provided using the HTTPS transport. The SOAP messages are secured using HTTPS. The CA certificate chain for the service's X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the service can be authenticated to the send port using the service's certificate.<br />-   **TransportWithMessageCredential**: Integrity, confidentiality, and service authentication are provided by the HTTPS transport. The CA certificate chain for the service's X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store on this computer so that the service can be authenticated to the send port using the service's certificate. The send port authentication is provided by SOAP message security.<br /><br /> The default is **None**.|  
    |**Transport client credential type**|Specify the type of credential to be used when performing the client authentication. Valid values include the following:<br /><br /> -   **None**: No authentication occurs at the transport level.<br />-   **Basic**: Basic authentication. In Basic authentication, user names and passwords are sent in plain text over the network. You must create the domain or local user accounts corresponding to the credentials.<br />-   **Digest**: Digest authentication. This authentication method operates much like Basic authentication, except that passwords are sent across the network as a hash value for additional security. Digest authentication is available only on domains with domain controllers running Windows Server operating systems authentication. You must create the domain or local user accounts corresponding to client credentials.<br />-   **Ntlm**: NTLM authentication. Clients can send the credentials without sending a password to this receive location. You must create the domain or local user accounts corresponding to client credentials.<br />-   **Windows**: Windows integrated authentication. Windows Communication Foundation negotiates Kerberos or NTLM, preferring Kerberos if a domain is present. If you want to use Kerberos it is important to have the client identify the service with a service principal name (SPN). You must create the domain or local user accounts corresponding to client credentials.<br />-   **Certificate**: Client authentication using the client certificate. The CA certificate chain for the client X.509 certificates must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the clients can be authenticated to this receive location. **Note:**  The **Transport client credential type** property must match the authentication scheme of the IIS virtual directory hosting this receive location. For example, if the property is set to **Windows**, you also need to enable **Integrated Windows authentication** for the virtual directory that hosts it. Similarly if the property is set to **None**, you must allow anonymous access to the virtual directory that hosts this receive location. <br /><br /> The default is **Windows**.|  
    |**Client certificate -  Thumbprint**|Specify the thumbprint of the X.509 certificate for authenticating this send port to the endpoint. You can select the thumbprint by navigating to the **My** store in the **Current User** location with the **Browse** button. **Note:**  You must install the client certificate into the **Current User** location of the user account for the send handler hosting this send port. <br /><br /> Minimum length: 0<br /><br /> Maximum length: 40<br /><br /> The default is an empty string.|  
    |**Service certificate - Thumbprint**|Specify the thumbprint of the X.509 certificate for authenticating the endpoint to which this send port sends messages. You can select the thumbprint navigating to the **Other People** store in the **Local Machine** location with the **Browse** button.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 40<br /><br /> The default is an empty string.|  
    |**User name credentials**|Specify the credentials for sending messages. You can specify the property by clicking the **Edit** button. You must set the credentials if you selected the **Username** option for **Message client credential type**.<br /><br /> The default value is **Do not use Single Sign-On**.|  
    |**Use ACS service identity**|Applies to [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] and BizTalk Server 2013. <br /><br />Select this checkbox and click **Edit** and provide the following values to authenticate with the Service Bus. This is required only when invoking a REST interface for Service Bus related entities.<br /><br /> -   **Access Control Service STS Uri** – Set this to `https://<Namespace>-sb.accesscontrol.windows.net/`, where \<namespace\> is your Service Bus namespace.<br />-   **Issuer Name** – Specify the issuer name. Typically this is set to owner.<br />-   **Issuer Key** – Specify the issuer key.|  
    |**Service Bus connection information** | New starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)].<br/><br/>Choose to use the Shared Access Signature (SAS) or Access Control Service (ACS) of the Service Bus namespace. <br/><br/>Select an option, and then select **Edit** to enter the key information:<br/><br/> - **Shared Access Signature** : Enter the access key name, and the access key. Both values are listed in the [Azure portal](https://portal.azure.com).<br/> - **Access Control Service** : Enter the STS URI (`https://<yourNamespace>-sb.accesscontrol.windows.net/`), Issuer name, and Issuer key. Use Windows PowerShell to retrieve these values, as described in [SB-Messaging adapter](../core/sb-messaging-adapter.md). |
  
6.  In the **Behavior** tab, configure the endpoint behavior for this send port. 

    |Use this|To do this|  
    |--------------|----------------|  
    | EndpointBehavior | Extend the funcionality of how requests are sent at the endpoint-level. You can add extensions that do different things, such as define the SOAP processing behavior, specify a time interval on transactions, control the discovery functionality, and use other .NET classes. <br/><br/>Right-select **EndpointBehavior**, and **Add Extension**. The list shows you the .NET classes that can be used. |
    
    This is similar to the endpoint behavior configuration for a WCF-Custom send port. See the **WCF-Custom Transport Properties Dialog Box, Send, Behavior** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
7.  In the **Proxy** tab, configure the proxy setting for the WCF-WebHttp send port. 
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Use send handler proxy settings**|Specify whether this send port uses the proxy settings in the send handler hosting this send port.<br /><br /> This is the default setting.|  
    |**Do not use proxy**|Indicate whether this send port uses a proxy server.<br /><br /> The default value is cleared.|  
    |**Use proxy**|Indicate whether this send port uses the proxy server specified in the **Address** property.<br /><br /> The default value is cleared.|  
    |**Address**|Specify the address of the proxy server. Use the **https** or the **http** scheme depending on the security configuration. This address can be followed by a colon and the port number. For example, http://127.0.0.1:8080.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
    |**User name**|Specify the user name to use for authentication. If integrated authentication is used, the user name includes the domain, that is, domain\username. If Basic or Digest authentication is used, the user name does not include domain\\. This property requires a value only if **Use proxy** is selected. **Note:**  The WCF-WebHttp send adapter uses the basic authentication for the proxy. <br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
    |**Password**|Specify the password to use for authentication.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
  
8.  In the **Messages** tab, specify how the message is sent to the REST interface.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Outbound HTTP Headers**|Specifies the HTTP headers that are stamped on the response message, if any.|  
    |**Suppress Body for Verbs**|Based on the verb you use to invoke a REST endpoint, you may or may not require a message payload. For example, you may not need a message payload while using the GET or DELETE verbs. However, to trigger a call to the REST endpoint using the send port, you may use a dummy message that includes a message payload. Before the message is sent to the REST endpoint, the message payload from the dummy message must be removed. You can specify the verbs for which the message payload must be removed using the **Suppress Body for Verbs** property.<br /><br /> For example, if you want to remove the message payload while using a GET verb, specify the value for this property as `GET`.|  
  
9. Click **OK** and **OK** again to save settings.  

## Import WCF extensions

Import WCF extensions in the receive handler or the send handler:

1.  In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration, expand [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  

2.  Select **WCF-WebHttp**, and then double-select the receive or send handler.  

3. In the General tab, select **Properties**. 

4. In **WCF Extensions**, select **Import**, and browse to the WCF extension config file. 

  
## Add a proxy to the send handler

You can add a proxy to the send port, or the send handler. If you are adding a proxy at the send port, then skip this section.

1.  In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  
  
2.  Select **WCF-WebHttp**, and then select the send handler.  
  
3.  In **Adapter Handler Properties**, on the **General** tab, select **Properties**.  
  
4.  In the **Proxy** tab, do the following.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Use proxy**|Indicate whether this send handler uses a proxy server.<br /><br /> The default value is cleared.|  
    |**Address**|Specify the address of the proxy server. Use the **https** or the **http** scheme depending on the security configuration. This address can be followed by a colon and the port number. For example, http://127.0.0.1:8080.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
    |**User name**|Specify the user name to use for authentication. If integrated or Basic authentication is used, the user name includes the domain, that is, domain\username. If Digest authentication is used, the user name does not include domain\\.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
    |**Password**|Specify the password to use for authentication.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
  
5.  Click **OK** until you exit all the dialog boxes.  
   
## See Also  
[SB-Messaging adapter](../core/sb-messaging-adapter.md)

[Using Adapters](../core/using-adapters.md)

[What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md)
