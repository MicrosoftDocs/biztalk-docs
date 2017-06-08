---
title: "WCF-WSHttp Transport Properties Dialog Box, Send, Binding Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-wshttp.transport.send.binding"
helpviewer_keywords: 
  - "WCF-WSHttp adapters, properties"
  - "bindings, WCF-WSHttp adapters"
  - "WCF-WSHttp adapters, bindings"
  - "properties, WCF-WSHttp adapters"
ms.assetid: 2093e122-91db-47e5-a970-46e03339e934
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-WSHttp Transport Properties Dialog Box, Send, Binding Tab
Use the **Binding** tab to configure the binding properties specific to the WCF-WSHttp send adapter.  The WCF-WSHttp adapter can communicate with a service through the WS-* standards over HTTP and HTTPS.  
  
> [!NOTE]
>  The current version of the WCF-WSHttp adapter does not support WS-Reliable Messaging.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Open timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Send timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a send operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**. If you use a solicit-response send port, this value specifies a time span for the whole interaction to complete, even if the service returns a large message.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Close timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Maximum received message size (bytes)**|Specify the maximum size, in bytes, for a message including headers, which can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br /><br /> Default value: 65536<br /><br /> Maximum value: 2147483647|  
|**Message encoding**|Specify the encoder used to encode the SOAP message. Valid values include the following:<br /><br /> -   **Text**: Use a text message encoder.<br />-   **Mtom**: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.<br /><br /> The default is **Text**.|  
|**Text encoding**|Specify the character set encoding to be used for emitting messages on the binding when the **Message encoding** property is set to **Text**. Valid values include the following:<br /><br /> -   **utf-16BE (unicodeFFFE)**: Unicode BigEndian encoding.<br />-   **utf-16**: 16-bit encoding.<br />-   **utf-8**: 8-bit encoding<br /><br /> The default is **utf-8**.|  
|**Enable transactions**|Specify whether a message is transmitted to the destination service and deleted from the MessageBox database in a transactional context using the **WS-AtomicTransaction** protocol.<br /><br /> The default value is cleared.|  
  
## See Also  
 [How to Configure a WCF-WSHttp Send Port](../core/how-to-configure-a-wcf-wshttp-send-port.md)