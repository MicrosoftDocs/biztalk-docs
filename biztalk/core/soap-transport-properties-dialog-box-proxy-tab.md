---
title: "SOAP Transport Properties Dialog Box, Proxy Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.soap.transport.proxy"
helpviewer_keywords: 
  - "SOAP adapters, properties"
  - "properties, SOAP adapters"
  - "SOAP adapters, proxies"
  - "proxies, SOAP adapters"
ms.assetid: 070aaab8-0b67-419d-816c-15fb2594c7f1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SOAP Transport Properties Dialog Box, Proxy Tab
In the **SOAP Transport Properties** dialog box, use the **Proxy** tab to configure the send port for the SOAP adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Use Handler's default proxy configuration**|Specify that the configuration for the send port uses the proxy handler.<br /><br /> This is the default setting.|  
|**Do not use proxy**|Indicate whether the SOAP send handler uses a proxy server.|  
|**Use proxy**|Indicate whether the SOAP send handler uses a proxy server.|  
|**Server**|Specifies the name of the proxy server.<br /><br /> This property only requires a value if Use proxy is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Port**|Specify the port the SOAP send handler uses.<br /><br /> This property only requires a value if Use proxy is selected.<br /><br /> Default Value: 80<br /><br /> Type: Long<br /><br /> Minimum value: 0<br /><br /> Maximum value: 65,535|  
|**User name**|Specify the user name to use for authentication. If integrated authentication is used, the user name includes the domain, domain\username. If Basic or Digest authentication is used, the user name does not include domain\\.<br /><br /> This property only requires a value if Use proxy is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Password**|Specify the password to use for authentication.<br /><br /> This property only requires a value if Use proxy is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
  
## See Also  
 [How to Configure a SOAP Send Port](../core/how-to-configure-a-soap-send-port.md)