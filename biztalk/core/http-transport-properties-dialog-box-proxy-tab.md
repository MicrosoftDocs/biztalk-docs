---
title: "HTTP Transport Properties Dialog Box, Proxy Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.http.transport.proxy"
helpviewer_keywords: 
  - "proxies, HTTP adapters"
  - "HTTP adapters, configuring"
  - "configuring, HTTP adapters"
  - "HTTP adapters, proxies"
ms.assetid: 9567b416-b440-46ff-bd9e-6960ea788b78
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Transport Properties Dialog Box, Proxy Tab
In the **HTTP Transport Properties** dialog box, use the **Proxy (Handler override)** tab to configure the send port for the HTTP adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Use Handler's default proxy configuration**|Specify that the configuration for the send port uses the proxy handler.<br /><br /> This is the default setting.|  
|**Do not use proxy**|Specify whether the HTTP send handler uses the proxy server.<br /><br /> If selected, the HTTP send handler does not use the proxy server.|  
|**Use proxy**|Specify whether the HTTP send handler uses the proxy server.<br /><br /> If selected, the HTTP send handler uses the proxy server.|  
|**Server**|Specify the proxy server address for this send port.<br /><br /> This property only requires a value if Use proxy is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Port**|Specify the proxy server port for this send port.<br /><br /> This property only requires a value if Use proxy is selected.<br /><br /> Default Value: 80<br /><br /> Type: Long<br /><br /> Minimum value: 0<br /><br /> Maximum value: 65535|  
|**User name**|Specify the user name for authentication with the proxy server.<br /><br /> This property only requires a value if Use proxy is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Password**|Specify the user password for authentication with the proxy server.<br /><br /> This property only requires a value if Use proxy is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
  
## See Also  
 [Configuring an HTTP Send Port](../core/configuring-an-http-send-port.md)