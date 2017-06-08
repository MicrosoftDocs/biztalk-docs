---
title: "&lt;Host Name&gt; Properties Dialog Box, Proxy Tab (WCF-WSHttp Adapter Send Handler) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-wshttp.sendhandler.proxy"
helpviewer_keywords: 
  - "WCF-WSHttp adapter, proxies"
  - "proxies, WCF-WSHttp adapters"
ms.assetid: 8d4b87d6-82b7-4410-99db-7a5c0f6084f5
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# &lt;Host Name&gt; Properties Dialog Box, Proxy Tab (WCF-WSHttp Adapter Send Handler)
Use the **Proxy** tab to configure the send handler for the WCF-WSHttp adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Use proxy**|Indicate whether this send port uses a proxy server.<br /><br /> The default value is cleared.|  
|**Address**|Specify the address of the proxy server. Use the **https** or the **http** scheme depending on the security configuration. This address can be followed by a colon and the port number. For example, http://127.0.0.1:8080.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**User name**|Specify the user name to use for authentication. If integrated authentication is used, the user name includes the domain, that is, domain\username. If Basic or Digest authentication is used, the user name does not include domain\\.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**Password**|Specify the password to use for authentication.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
  
## See Also  
 [How to Configure a WCF-WSHttp Send Handler](../core/how-to-configure-a-wcf-wshttp-send-handler.md)