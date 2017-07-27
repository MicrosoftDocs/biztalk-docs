---
title: "WCF-BasicHttp Transport Properties Dialog Box, Send, Proxy Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-basichttp.transport.send.proxy"
helpviewer_keywords: 
  - "proxies, WCF-BasicHttp adapters"
  - "WCF-BasicHttp adapters, properties"
  - "properties, WCF-BasicHttp adapters"
  - "WCF-BasicHttp adapters, proxies"
ms.assetid: ca3e9dde-982c-47cc-8ec0-1fbe11506641
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-BasicHttp Transport Properties Dialog Box, Send, Proxy Tab
Use the **Proxy** tab to configure the proxy for this send port.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Use Handler's default proxy settings**|Specify whether this send port uses the proxy settings in the send handler hosting this send port.<br /><br /> This is the default setting.|  
|**Do not use proxy**|Indicate whether this send port uses a proxy server.<br /><br /> The default value is cleared.|  
|**Use proxy**|Indicate whether this send port uses the proxy server specified in the **Address** property.<br /><br /> The default value is cleared.|  
|**Address**|Specify the address of the proxy server. Use the **https** or the **http** scheme depending on the security configuration. This address can be followed by a colon and the port number. For example, http://127.0.0.1:8080.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**User name**|Specify the user name to use for authentication. If integrated authentication is used, the user name includes the domain, that is, domain\username. If Basic or Digest authentication is used, the user name does not include domain\\. This property requires a value only if **Use proxy** is selected. **Note:**  The WCF-BasicHttp send adapter uses the basic authentication for the proxy. <br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
|**Password**|Specify the password to use for authentication.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
  
## See Also  
 [How to Configure a WCF-BasicHttp Send Port](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f)   
 [How to Configure a WCF-BasicHttp Send Handler](http://msdn.microsoft.com/library/18dcc616-4732-42f8-bd64-e55a5ebbaa49)