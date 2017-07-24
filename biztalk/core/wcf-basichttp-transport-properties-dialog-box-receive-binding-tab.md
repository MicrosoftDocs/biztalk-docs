---
title: "WCF-BasicHttp Transport Properties Dialog Box, Receive, Binding Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-basichttp.transport.receive.binding"
helpviewer_keywords: 
  - "WCF-BasicHttp adapters, bindings"
  - "WCF-BasicHttp adapters, properties"
  - "properties, WCF-BasicHttp adapters"
  - "bindings, WCF-BasicHttp adapters"
ms.assetid: bd29d41c-3c83-447d-a01e-310ea3467905
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-BasicHttp Transport Properties Dialog Box, Receive, Binding Tab
Use the **Binding** tab to define the binding properties specific to the WCF-BasicHttp receive adapter. The WCF-BasicHttp receive adapter can use to communicate with WS-I Basic Profile 1.1-conformant Web services like ASMX-based services.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Open timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Send timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a send operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**. If you use a request-response receive port, this value specifies a time span for the whole interaction to complete, even if the client returns a large message.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Close timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Maximum received message size (bytes)**|Specify the maximum size, in bytes, for a message including headers, which can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br /><br /> The WCF-BasicHttp adapter leverages the [BasicHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81086) class in the buffered transfer mode to communicate with an endpoint. For the buffered transport mode, the [BasicHttpBinding.MaxBufferSize](http://go.microsoft.com/fwlink/?LinkId=80659) property is always equal to the value of this property.<br /><br /> Default value: 65536<br /><br /> Maximum value: 2147483647|  
|**Message encoding**|Specify the encoder used to encode the SOAP message. Valid values include the following:<br /><br /> -   **Text**: Use a text message encoder.<br />-   **Mtom**: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.<br /><br /> The default is **Text**.|  
|**Text encoding**|Specify the character set encoding to be used for emitting messages on the binding when the **Message encoding** property is set to **Text**. Valid values include the following:<br /><br /> -   **utf-16BE (unicodeFFFE)**: Unicode BigEndian encoding.<br />-   **utf-16**: 16-bit encoding.<br />-   **utf-8**: 8-bit encoding<br /><br /> The default is **utf-8**.|  
|**Max concurrent calls**|Specify the number of concurrent calls to a single service instance. Calls in excess of the limit are queued. Setting this value to 0 is equivalent to setting it to **Int32.MaxValue**.<br /><br /> The default is 200|  
  
## See Also  
 [How to Configure a WCF-BasicHttp Receive Location](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)