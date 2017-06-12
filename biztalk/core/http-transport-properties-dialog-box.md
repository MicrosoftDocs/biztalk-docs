---
title: "HTTP Transport Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.http.transport"
helpviewer_keywords: 
  - "receive locations, HTTP adapters"
  - "HTTP adapters, configuring"
  - "configuring, HTTP adapters"
  - "HTTP adapters, receive locations"
ms.assetid: aa3a9d4d-56d6-4db8-8636-347bd0293653
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Transport Properties Dialog Box
Use the **HTTP Transport Properties** dialog box to configure the receive location for the HTTP adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Virtual directory plus ISAPI extension**|Specify the name of the virtual directory where you post the messages received by the HTTP/HTTPS receive location. The virtual directory includes the name of the receive location DLL and an optional query string. Examples of virtual directory names are:<br /><br /> /\<virtual directory>/BTSHTTPReceive.dll<br /><br /> /\<virtual directory>/BTSHTTPReceive.dll?Purchase%20Order<br /><br /> This location must not contain more than one BTSHTTPReceive.dll ISAPI extension, including all subfolders.<br /><br /> Type: String<br /><br /> Maximum length: 256|  
|**Public address**|Specify the fully qualified URI for this receive location. The value for this property is a combination of the server name and the virtual directory. This address is exposed to external partners.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Return content type**|Specify the content type of HTTP response messages that the receive location sends back to clients. This property is valid only for request-response receive locations.<br /><br /> Default value: text/xml<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Loopback**|Define that the request message received on this location is routed either to a send port or back to this receive location to be sent as a response. This property is valid only for request-response receive locations.<br /><br /> Default value: False<br /><br /> Type: Boolean|  
|**Return correlation handle on success (this setting is for one-way port only)**|Define that if successful, the receive location sends the correlation token of the submitted message on the HTTP response to the client. This property is valid only for one-way receive locations.<br /><br /> Default value: True<br /><br /> Type: Boolean|  
|**Use Single Sign-On**|Indicate that Enterprise Single Sign-On is used.<br /><br /> Default value: False<br /><br /> Type: Boolean|  
|**Suspend failed requests**|Indicate whether to suspend an HTTP request that fails inbound processing due to a receive pipeline failure or a routing failure.<br /><br /> Default value: False<br /><br /> Type: Boolean|  
  
## See Also  
 [How to Configure an HTTP Receive Location](../core/how-to-configure-an-http-receive-location.md)   
 [Configuring the HTTP Adapter](../core/configuring-the-http-adapter.md)