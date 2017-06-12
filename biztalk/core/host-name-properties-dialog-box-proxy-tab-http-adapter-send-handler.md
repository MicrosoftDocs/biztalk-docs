---
title: "&lt;Host Name&gt; Properties Dialog Box, Proxy Tab (HTTP Adapter Send Handler) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.proxy.props1"
helpviewer_keywords: 
  - "proxies, HTTP adapters"
  - "send handlers, HTTP adapters"
  - "HTTP adapters, proxies"
  - "HTTP adapters, send handlers"
ms.assetid: 54aee60f-6cc6-4fd7-a6d5-59ac94a8fa83
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# &lt;Host Name&gt; Properties Dialog Box, Proxy Tab (HTTP Adapter Send Handler)
Use the **Proxy** tab to configure the send handler for the HTTP adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Use proxy**|Specify whether the HTTP send handler uses the proxy server.<br /><br /> Default value: False<br /><br /> Type: Boolean|  
|**Server**|Specify the proxy server address for this send port.<br /><br /> This property requires a value if Use proxy is True.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Port**|Specify the proxy server port for this send port.<br /><br /> This property requires a value if Use proxy is True.<br /><br /> Default Value: 80<br /><br /> Type: Long<br /><br /> Minimum value: 0<br /><br /> Maximum value: 65535|  
|**User name**|Specify the user name to use for authentication with the proxy server.<br /><br /> This property requires a value if Use proxy is True.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Password**|Specify the user password for authentication with the proxy server.<br /><br /> This property requires a value if Use proxy is True.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
  
## See Also  
 [How to Configure an HTTP Send Handler](../core/how-to-configure-an-http-send-handler.md)