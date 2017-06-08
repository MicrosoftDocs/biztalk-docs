---
title: "WCF-WSHttp Transport Properties Dialog Box, Send, Proxy Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-wshttp.transport.send.proxy"
helpviewer_keywords: 
  - "WCF-WSHttp adapters, properties"
  - "proxies, WCF-WSHttp adapters"
  - "WCF-WSHttp adapters, proxies"
  - "properties, WCF-WSHttp adapters"
ms.assetid: 40f2ae93-add8-4963-8aa1-f798b829d026
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-WSHttp Transport Properties Dialog Box, Send, Proxy Tab
Use the **Proxy** tab to configure the proxy for this send port.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Use Handler's default proxy settings**|Specify whether this send port uses the proxy settings in the send handler hosting this send port.<br /><br /> This is the default setting.|  
|**Do not use proxy**|Indicate whether this send port uses a proxy server.<br /><br /> The default value is cleared.|  
|**Use proxy**|Indicate whether this send port uses the proxy server specified in the **Address** property.<br /><br /> The default value is cleared.|  
|**Address**|Specify the address of the proxy server. Specify the address of the proxy server. Use the **https** or the **http** scheme depending on the security configuration. This address can be followed by a colon and the port number. For example, http://127.0.0.1:8080.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**User name**|Specify the user name to use for authentication. If integrated authentication is used, the user name includes the domain, that is, domain\username. If Basic or Digest authentication is used, the user name does not include domain\\. This property requires a value only if **Use proxy** is selected. **Note:**  The WCF-WSHttp send adapter uses the basic authentication for the proxy. <br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**Password**|Specify the password to use for authentication.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
  
## See Also  
 [How to Configure a WCF-WSHttp Send Port](../core/how-to-configure-a-wcf-wshttp-send-port.md)   
 [How to Configure a WCF-WSHttp Send Handler](../core/how-to-configure-a-wcf-wshttp-send-handler.md)