---
title: "SOAP Adapter Configuration Properties | Microsoft Docs"
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
  - "SOAP adapters, properties"
  - "receive locations, adapters"
  - "SOAP adapters, receive locations"
  - "send ports, adapters"
ms.assetid: 0d033371-ee31-4e43-a7d3-e0975791d981
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SOAP Adapter Configuration Properties
The following table lists the configuration properties that you can set for a SOAP adapter receive location:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|UseSSO|VT_BOOL|Specify whether to use Single Sign-On.|-   Valid values are:<br />-   -1 (true)<br />-   0 (false)|The default value is 0 (false).|  
  
 The following code shows the format of the XML string you use to set the properties:  
  
```  
<CustomProps>  
<UseSSO vt="11">0</UseSSO>  
</CustomProps>  
```  
  
 The following table lists the configuration properties that you can set for a SOAP adapter send port:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|ProxyPort|VT_I4|Specify the proxy server port for this send port.|None|This property does not require a value unless the UseProxy property is set to -1 (true).<br /><br /> The default value is 80.|  
|AuthenticationScheme|VT_BSTR|Specify the type of authentication to use with the destination server.|Valid values are:<br /><br /> -   Anonymous<br />-   Basic<br />-   Digest<br />-   NTLM|The default value is Anonymous.|  
|Username|VT_BSTR|Specify the user name to use for authentication with the destination server.|Minimum length: 0<br /><br /> Maximum length: 256|This property does not require a value unless the AuthenticationScheme property is set to Basic or Digest and the UseSSO property is set to 0 (false).|  
|UseProxy|VT_BOOL|Specify whether the SOAP send handler uses a proxy server.|Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is 0 (false).|  
|UseSoap12|VT_BOOL|Specify to generate proxy code that will support the SOAP 1.2 protocol.|If this option is not selected, SOAP 1.1-compliant proxy code will be generated.<br /><br /> Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is 0 (false).|  
|UsingOrchestration|VT_BOOL|Specify whether to use the Web service proxy associated with the address for this send port.|Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is -1 (true).|  
|UseSSO|VT_BOOL|Specify that Enterprise Single Sign-On is used.|Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is 0 (false).|  
|ProxyAddress|VT_BSTR|Specify the name of the proxy server.|This property is only valid if the UseProxy property is set to -1 (true).|None|  
|Password|VT_NULL|Specify the password to use for authentication with the destination server.|This value is always set to null when exporting a binding file. This field must be manually populated with the password before importing the binding file into the target BizTalk Server configuration.|This property does not require a value unless the AuthenticationScheme property is set to Basic or Digest and the UseSSO property is set to 0 (false).|  
|AssemblyPath|VT_BSTR|Specify the path to the assembly containing the Web service proxy.|None|None|  
|TypeName|VT_BSTR|Specify the name of the class that contains the Web method to be invoked.|None|None|  
|MethodName|VT_BSTR|Specify the method of the class that will be invoked.|None|None|  
|UseHandlerSetting|VT_BOOL|Specify whether to use the SOAP send handler's default proxy configuration.|Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is -1 (true).|  
|ClientCertificate|VT_BSTR|Specify the thumbprint of the client certificate to use for establishing a connection.|Minimum length: 0<br /><br /> Maximum length: 59|None|  
|ProxyPassword|VT_NULL|Specify the password to use for authentication with the proxy server.|This value is always set to null when exporting a binding file. This field must be manually populated with the password before importing the binding file into the target BizTalk Server configuration.|This property does not require a value if UseProxy is set to 0 (false).|  
|ProxyUsername|VT_BSTR|Specify the username to use for authentication with the proxy server.|None|This property does not require a value unless the UseProxy property is set to -1 (true).|  
  
 The following code shows the format of the XML string you use to set the properties:  
  
```  
<CustomProps>  
<ProxyPort vt="3">80</ProxyPort>  
<AuthenticationScheme vt="8">Basic</AuthenticationScheme>  
<Username vt="8">domain\testuser</Username>  
<UseProxy vt="11">-1</UseProxy>  
<UseSoap12 vt="11">-1</UseSoap12>  
<UsingOrchestration vt="11">-1</UsingOrchestration>  
<UseSSO vt="11">0</UseSSO>  
<ProxyAddress vt="8">proxy</ProxyAddress>  
<Password vt="1" />  
<ProxyPort vt="3">80</ProxyPort>  
<AssemblyPath vt="8">C:\Websvc.dll</AssemblyPath>  
<TypeName vt="8">Websvc.svc</TypeName>  
<MethodName vt="8">WebMethod</MethodName>  
<UseHandlerSetting vt="11">0</UseHandlerSetting></  
<ClientCertificate vt="8">23779A5EEA9693A37409021EFCDAB713A3680C34</ClientCertificate>  
<ProxyPassword vt="1" />  
<ProxyUsername vt="8">proxyuser</ProxyUsername>  
</CustomProps>  
```