---
title: "HTTP Transport Properties Dialog Box, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.http.transport.general"
helpviewer_keywords: 
  - "HTTP adapters, configuring"
  - "configuring, HTTP adapters"
ms.assetid: bfec6b41-c556-4f10-9d42-0815b655f686
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Transport Properties Dialog Box, General Tab
In the **HTTP Transport Properties** dialog box, use the **General**tab to configure the send port for the HTTP adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Destination URL**|Required. Specify the address to send HTTP requests. Include query strings appended to the base URL.<br /><br /> Type: String<br /><br /> Maximum length: 256|  
|**Enable chunked encoding**|It is an optimization done for http protocol. If it is selected, the http adapter will use chunked transfer encoding.<br /><br /> Valid values are:<br /><br /> True (checked) The http adapter will use chunked transfer encoding.<br /><br /> False (not checked) The http adapter will not use chunked transfer encoding.<br /><br /> Default Value: True|  
|**Request timeout (sec)**|Specify the time-out in seconds for the HTTP/HTTPS transmission. If the response is not received within this time, the service logs the error and resubmits the message based on the retry infrastructure.<br /><br /> If set to zero (0), then the time-out is calculated based on the request message size. If the value is not provided, then the value for the handler is used.<br /><br /> Type: Long<br /><br /> Minimum value: 0<br /><br /> Maximum value: MAX_LONG|  
|**Maximum redirects**|This property is not implemented by the HTTP send port.|  
|**Content type**|Specify the content type of the request messages.<br /><br /> If this value is not set, then the value for the handler is used.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
  
## See Also  
 [Configuring an HTTP Send Port](../core/configuring-an-http-send-port.md)   
 [Restrictions on the Destination URL Property](../core/restrictions-on-the-destination-url-property.md)