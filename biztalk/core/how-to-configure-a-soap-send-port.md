---
title: "How to Configure a SOAP Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SOAP adapters, send ports"
  - "SOAP adapters, code samples"
  - "code samples, SOAP adapters"
  - "configuring [SOAP adapters], code samples"
  - "configuring [SOAP adapters], send ports"
  - "send ports, SOAP adapters"
ms.assetid: 3a0622f4-d25d-4449-a063-d8ba217e9729
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a SOAP Send Port
You can configure a SOAP send port either programmatically or by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  

 **How to Configure a SOAP Send Port Programmatically**  

 The BizTalk Explorer object model exposes an adapter-specific interface for send ports named **ITransportInfo** that has the **TransportTypeData** read/write property. This property accepts a SOAP send port configuration property bag in the form of a name-value pair of XML strings. Note that to set this property in the BizTalk Explorer object model you must set the **OutboundTransportLocation** property of the **ITransportInfo** interface first.  

 The **TransportTypeData** property of the **ITransportInfo** interface is not required. If it is not set, the adapter uses the default values for the SOAP send port configuration, as indicated in the following table.  

 The following table lists the configuration properties you can set in the BizTalk Explorer object model for SOAP send ports.  

|Property name|Type|Description|  
|-------------------|----------|-----------------|  
|**URI**|String|Virtual directory containing the Web service on the deployment server.|  
|**Username**|String|User name to specify for accessing the target Web service.<br /><br /> Default value: Blank|  
|**Password**|String|User password to use for authentication with the server.<br /><br /> Default value: Blank|  
|**ClientCertificate**|String|Thumbprint of client SSL certificate.<br /><br /> Default value: Blank|  
|**AffiliateApplicationName**|String|The name of the SSO application to use to redeem the ticket for client credentials.<br /><br /> The **AffiliateApplicationName** is mutually exclusive to a **Username** and **Password** pair.<br /><br /> Default value: Blank|  
|**UseProxy**|Boolean|Indicates whether the SOAP send port uses a proxy server to access the target Web service. The proxy server can be shared by all SOAP send ports.<br /><br /> Default value: False|  
|**ProxyAddress**|String|Address of the HTTP proxy to use for the Web service call.<br /><br /> Default value: Blank|  
|**ProxyPort**|Integer|Port of the HTTP proxy to use for the Web service call.<br /><br /> Default value: Blank|  
|**ProxyUsername**|String|User name to use for the proxy.<br /><br /> Default value: Blank|  
|**ProxyPassword**|String|Password to use for the proxy.<br /><br /> Default value: Blank|  

 The following code shows the format to use to set these properties:  

```  
<CustomProps>  
   <URI vt="8"/>  
   <ClientCertificate vt="8"/>  
   <Password vt="8">Encrypted</Password>  
   <ProxyAddress vt="8"/>  
   <ProxyPassword vt="8">Encrypted</ProxyPassword>  
   <ProxyPort vt="3"/>  
   <ProxyUsername vt="8"/>  
   <UseProxy vt="11"/>  
   <Username vt="8"/>  
   <AffiliateApplicationName vt="8"/>  
</CustomProps>  
```  

 **How to Configure a SOAP Send Port with the BizTalk Server Administration Console**  

 You can set SOAP send port adapter variables in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. If properties are not set for the send port, the default send handler values set in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console are used.  

### To configure variables for a SOAP send port  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a new send port or double-click an existing send port to modify it. For more information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). Configure all of the send port options and specify **SOAP** for the **Type** option in the **Transport** section of the **General** tab.  

2. On the **General** tab, in the **Transport** section next to **Type**, click **Configure**.  

3. In the **SOAP Transport Properties** dialog box, on the **General** tab, do the following:  


   |             Use this              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     To do this                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
   |-----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        **Web Service URL**        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   Specify the address of the Web service you want to call. **Note:**  The URI for a send port or receive location cannot exceed 256 characters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |        **Authentication**         |                                                                                                                                                                                                                                                                                                                                                                                                                          Indicate the authentication method used by the Web service you are calling.<br /><br /> Options:<br /><br /> -   **Anonymous .** The default setting.<br />-   **Basic .** The SOAP connection sends the user name and password in plain text.<br />-   **Digest .** The SOAP connection sends the password in an encrypted format.<br />-   **NTLM .** Neither the user name nor the password is sent over a SOAP connection. The SOAP adapter always uses the credentials of the process under which the SOAP send adapter runs for this authentication type.                                                                                                                                                                                                                                                                                                                                                                                                                           |
   |          **Credentials**          | Specify the type of credentials to use.<br /><br /> Only available if the **Authentication type** is **Basic** or **Digest**.<br /><br /> Options:<br /><br /> -   **Do Not Use Single Sign-On**<br />     **User name**<br />     The user name to use for authentication with the destination server. If the **Authentication type** property is **Anonymous** or **NTLM**, this option is disabled. This property requires a value if **Basic** or **Digest** is selected, and Enterprise Single Sign-On is not used.<br />     Minimum length: 0<br />     Maximum length: 256<br />     **Password**<br />     The password to use for authentication with the destination server. If the **Authentication type** property is **Anonymous** or **NTLM**, this option is disabled. This property requires a value if **Basic** or **Digest** is selected, and Single Sign-On is not used.<br />     Minimum length: 0<br />     Maximum length: 256<br />-   **Use Single Sign-On**<br />     Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.<br />     **Affiliate Application**<br />     Specifies the affiliate application to use for Single Sign-On. For information about populating this list, see [SSO Affiliate Applications](../core/sso-affiliate-applications.md).<br />     Minimum length: 0<br />     Maximum length: 256 |
   | **Client Certificate Thumbprint** |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Specify the thumbprint of the client certificate to use for establishing a connection.<br /><br /> Example: 01 23 45 67 89 AB CD EF 01 23 45 67 89 AB CD EF 01 23 45 67<br /><br /> Minimum length: 0<br /><br /> Maximum length: 59                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |


4. In the **SOAP Transport Properties** dialog box, on the **Proxy** tab, do the following:  


   |                   Use this                    |                                                                                                                                                                                                     To do this                                                                                                                                                                                                      |
   |-----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Use Handler's default proxy configuration** |                                                                         Specify the send port proxy handler configuration. When true, the port will use the proxy settings specified at the handler level. When false, the send adapter will use the proxy information specified on the send port.<br /><br /> The default setting is true.                                                                         |
   |             **Do not use proxy**              |                                                                                                                                                                             Indicate whether the SOAP send handler uses a proxy server.                                                                                                                                                                             |
   |                 **Use proxy**                 |                                                                                                                                                 Indicate whether the SOAP send handler uses a proxy server. The proxy server can be shared by all SOAP send ports.                                                                                                                                                  |
   |                  **Server**                   |                                                                                                    Specifies the name of the proxy server.<br /><br /> This property only requires a value if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256                                                                                                     |
   |                   **Port**                    |                                       Specify the port the SOAP send handler uses.<br /><br /> This property only requires a value if **Use proxy** is selected.<br /><br /> Default Value: 80<br /><br /> Type: Long<br /><br /> Minimum value: 0<br /><br /> Maximum value: 65535 **Note:**  Specifying a value of 0 indicates to use the default value, which is port 80.                                        |
   |                 **User name**                 | Specify the user name to use for authentication. If you use Windows integrated authentication, the user name includes the domain, **domain\username**. If you use Basic or Digest authentication, the user name does not include **domain\\**.<br /><br /> This property only requires a value if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256 |
   |                 **Password**                  |                                                                                                Specify the password to use for authentication.<br /><br /> This property only requires a value if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256                                                                                                 |


5. In the **SOAP Transport Properties** dialog box, on the **Web Service** tab, do the following:  


   |          Use this          |                                                                                                                                                                                                  To do this                                                                                                                                                                                                  |
   |----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Orchestration Web Port** |                                                                                                                                Specify to use the Web service that is exposed at the Web Service URL listed on the **General** tab.<br /><br /> This is the default setting.                                                                                                                                 |
   |     **Assembly name**      | Specify the name of the assembly containing the Web service proxy. This field can be populated by clicking the browse button to find an assembly. After selecting the assembly this box is populated with the fully qualified name of the assembly. **Note:**  The specified assembly must be present on all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s at runtime. |
   |       **Type name**        |                                                                                                                              Specify the name of the class that contains the Web method to be invoked. This can be selected from a list of types contained within the assembly.                                                                                                                              |
   |      **Method name**       |                                             Specify one of the methods in the list box or choose the option to "Specify later". If the option to "Specify later" is chosen, the Web method must be set by some other means, such as a pipeline component. In this scenario, the web method must be written to the Soap Adapter **MethodName** context property.                                              |
   |        **SOAP 1.2**        |                                                                                                         Specify to generate proxy code that will support the SOAP 1.2 protocol. If this option is left cleared, SOAP 1.1-compliant proxy code will be generated.<br /><br /> Default value: cleared                                                                                                          |


6. Click **OK** and **OK** again to save settings.  

## See Also  
 [Publishing Web Services](../core/publishing-web-services.md)