---
title: "WCF-WSHttp Transport Properties Dialog Box, Receive, Binding Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-wshttp.transport.receive.binding"
helpviewer_keywords: 
  - "WCF-WSHttp adapters, properties"
  - "bindings, WCF-WSHttp adapters"
  - "WCF-WSHttp adapters, bindings"
  - "properties, WCF-WSHttp adapters"
ms.assetid: 16ccffe5-c047-4bb8-9247-a1cb178b5b06
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-WSHttp Transport Properties Dialog Box, Receive, Binding Tab
Use the **Binding** tab to define the binding properties specific to the WCF-WSHttp receive adapter. The WCF-WSHttp receive adapter can use to communicate with a service through the WS-* standards over HTTP and HTTPS.  
  
> [!NOTE]
>  The current version of the WCF-WSHttp adapter does not support WS-Reliable Messaging.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Open timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Send timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a send operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**. If you use a request-response receive port, this value specifies a time span for the whole interaction to complete, even if the client returns a large message.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Close timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Maximum received message size (bytes)**|Specify the maximum size, in bytes, for a message including headers, which can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br /><br /> Default value: 65536<br /><br /> Maximum value: 2147483647|  
|**Message encoding**|Specify the encoder used to encode the SOAP message. Valid values include the following:<br /><br /> -   **Text**: Use a text message encoder.<br />-   **Mtom**: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.<br /><br /> The default is **Text**.|  
|**Text encoding**|Specify the character set encoding to be used for emitting messages on the binding when the **Message encoding** property is set to **Text**. Valid values include the following:<br /><br /> -   **utf-16BE (unicodeFFFE)**: Unicode BigEndian encoding.<br />-   **utf-16**: 16-bit encoding.<br />-   **utf-8**: 8-bit encoding<br /><br /> The default is **utf-8**.|  
|**Enable transactions**|Specify whether a message is submitted to the MessageBox database using the transaction flowed from clients. If this property is set, the clients are required to submit messages using the **WS-AtomicTransaction** protocol. If the clients submit messages outside the transactional scope then this receive location returns an exception back to the clients, and no messages are suspended.<br /><br /> The option is available only for one-way receive locations. If the clients submit messages in a transactional context for request-response receive locations, then an exception is returned back to the clients and no messages are suspended.<br /><br /> The default value is cleared.|  
|**Max concurrent calls**|Specify the number of concurrent calls to a single service instance. Calls in excess of the limit are queued. Setting this value to 0 is equivalent to setting it to **Int32.MaxValue**.<br /><br /> The default is 200|  
  
## Transaction Semantics on Message Failures  
 The following table describes the semantics of transactional message submission on message failures during inbound processing.  
  
|Message submission result|Is the message suspended on failure?|Vote on the transaction outcome|Return result|  
|-------------------------------|------------------------------------------|-------------------------------------|-------------------|  
|Failure|Yes|Commit|Error|  
|Failure|No|Abort|Error|  
|Success|Yes|Commit|Success|  
|Success|No|Commit|Success|  
  
## See Also  
 [How to Configure a WCF-WSHttp Receive Location](../core/how-to-configure-a-wcf-wshttp-receive-location.md)