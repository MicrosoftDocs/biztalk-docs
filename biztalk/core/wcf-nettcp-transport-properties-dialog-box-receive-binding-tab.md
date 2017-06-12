---
title: "WCF-NetTcp Transport Properties Dialog Box, Receive, Binding Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-nettcp.transport.receive.binding"
helpviewer_keywords: 
  - "WCF-NetTcp adapters, bindings"
  - "properties, WCF-NetTcp adapters"
  - "bindings, WCF-NetTcp adapters"
  - "WCF-NetTcp adapters, properties"
ms.assetid: f7c2ca6b-ba68-47d4-88f9-847547aa22da
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-NetTcp Transport Properties Dialog Box, Receive, Binding Tab
Use the **Binding** tab to define the binding properties specific to the WCF-NetTcp receive adapter. The WCF-NetTcp receive adapter can use to communicate with service through the WS-* standards over the TCP transport.  
  
> [!NOTE]
>  The current version of the WCF-NetTcp adapter does not support WS-Reliable Messaging.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Open timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Send timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a send operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**. If you use a request-response receive port, this value specifies a time span for the whole interaction to complete, even if the client returns a large message.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Close timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Maximum received message size (bytes)**|Specify the maximum size, in bytes, for a message including headers, which can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br /><br /> The WCF-NetTcp adapter leverages the [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) class in the buffered transfer mode to communicate with an endpoint. For the buffered transport mode, the [NetTcpBinding.MaxBufferSize](http://go.microsoft.com/fwlink/?LinkId=81088) property is always equal to the value of this property.<br /><br /> Default value: 65536<br /><br /> Maximum value: 2147483647|  
|**Enable transactions**|Specify whether a message is submitted to the MessageBox database using the transaction flowed from clients. If this property is set, the clients are required to submit messages using the transaction protocol specified in the **Transaction protocol** property. If the clients submit messages outside the transactional scope then this receive location returns an exception back to the clients, and no messages are suspended.<br /><br /> The option is available only for one-way receive locations. If the clients submit messages in a transactional context for request-response receive locations, then an exception is returned back to the clients and no messages are suspended.<br /><br /> The default value is cleared.|  
|**Transaction protocol**|Specify the transaction protocol to be used with this receive location. Valid values include the following:<br /><br /> -   **OleTransaction**<br />-   **WS-AtomicTransaction**<br /><br /> The default is **OleTransaction**.|  
|**Lease timeout (hh:mm:ss)**|Specify maximum lifetime of an active pooled connection. After the specified time elapses, the connection closes once the current request is serviced.<br /><br /> The WCF-NetTcp adapter leverages the [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) class to communicate with an endpoint. When using the [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) in load-balanced scenarios, consider reducing the default lease timeout. For more information about the load balancing when using the [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087), see the appropriate topic in See Also.<br /><br /> Default value: 00:05:00<br /><br /> Maximum value:  23:59:59|  
|**Maximum concurrent calls**|Specify the number of concurrent calls to a single service instance. Calls in excess of the limit are queued. Setting this value to 0 is equivalent to setting it to **Int32.MaxValue**.<br /><br /> Default value: 200|  
  
## Transaction Semantics on Message Failures  
 The following table describes the semantics of transactional message submission on message failures during inbound processing:  
  
|Message submission result|Is the message suspended on failure?|Vote on the transaction outcome|Return result|  
|-------------------------------|------------------------------------------|-------------------------------------|-------------------|  
|Failure|Yes|Commit|Error|  
|Failure|No|Abort|Error|  
|Success|Yes|Commit|Success|  
|Success|No|Commit|Success|  
  
## See Also  
 [How to Configure a WCF-NetTcp Receive Location](../core/how-to-configure-a-wcf-nettcp-receive-location.md)   
 [Load Balancing](http://go.microsoft.com/fwlink/?LinkId=81089)