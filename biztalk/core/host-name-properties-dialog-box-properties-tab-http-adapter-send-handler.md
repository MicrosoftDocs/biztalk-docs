---
title: "&lt;Host Name&gt; Properties Dialog Box, Properties Tab (HTTP Adapter Send Handler) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.http.handler.send.props"
helpviewer_keywords: 
  - "send handlers, HTTP adapters"
  - "HTTP adapters, properties"
  - "properties, HTTP adapters"
  - "properties, configuring [HTTP adapters]"
  - "HTTP adapters, send handlers"
ms.assetid: e1395497-2631-4c1a-b40c-7e1d66c115ea
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# &lt;Host Name&gt; Properties Dialog Box, Properties Tab (HTTP Adapter Send Handler)
In the **\<Host Name> Properties** dialog box, use the Properties tab to configure the send handler for the HTTP adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Request timeout (sec)**|Specify the time-out in seconds when waiting for a response from the server.<br /><br /> If set to zero (0), then the time-out is calculated based on the request message size.<br /><br /> If a value is not provided, then the value for the handler is used.<br /><br /> Default Value: 0<br /><br /> Type: Long<br /><br /> Minimum value: 0<br /><br /> Maximum value: MAX_LONG|  
|**Maximum redirects**|Specify the maximum redirects allowed for the message being sent.<br /><br /> Default value: 5<br /><br /> Type:<br /><br /> Minimum value: 0<br /><br /> Maximum value: MAX_LONG|  
|**Content type**|Specify the content type of the request messages.<br /><br /> If a value is not provided, then the value for the handler is used.<br /><br /> Default value: text/xml<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
  
## See Also  
 [How to Configure an HTTP Send Handler](../core/how-to-configure-an-http-send-handler.md)