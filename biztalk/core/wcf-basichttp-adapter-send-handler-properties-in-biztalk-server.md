---
title: "&lt;Host Name&gt; Properties Dialog Box, Proxy Tab (WCF-BasicHttp Adapter Send Handler) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-basichttp.sendhandler.proxy"
helpviewer_keywords: 
  - "proxies, WCF-BasicHttp adapters"
  - "WCF-BasicHttp adapters, proxies"
ms.assetid: acea821f-2941-4498-94d6-12e5ff1b76d3
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# &lt;Host Name&gt; Properties Dialog Box, Proxy Tab (WCF-BasicHttp Adapter Send Handler)
Use the **Proxy** tab to configure the send handler for the WCF-BasicHttp adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Use proxy**|Indicate whether this send port uses a proxy server.<br /><br /> The default value is cleared.|  
|**Address**|Specify the address of the proxy server. Specify the address of the proxy server. Use the **https** or the **http** scheme depending on the security configuration. This address can be followed by a colon and the port number. For example, http://127.0.0.1:8080.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**User name**|Specify the user name to use for authentication. If integrated authentication is used, the user name includes the domain, that is, domain\username. If Basic or Digest authentication is used, the user name does not include domain\\.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**Password**|Specify the password to use for authentication.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
  
## See Also  
 [How to Configure a WCF-BasicHttp Send Handler](http://msdn.microsoft.com/library/18dcc616-4732-42f8-bd64-e55a5ebbaa49)