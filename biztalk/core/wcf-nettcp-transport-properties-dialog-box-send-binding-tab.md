---
title: "WCF-NetTcp Transport Properties Dialog Box, Send, Binding Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-nettcp.transport.send.binding"
helpviewer_keywords: 
  - "WCF-NetTcp adapters, bindings"
  - "properties, WCF-NetTcp adapters"
  - "bindings, WCF-NetTcp adapters"
  - "WCF-NetTcp adapters, properties"
ms.assetid: ca2f3b64-d646-475e-a745-e767e39e6941
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-NetTcp Transport Properties Dialog Box, Send, Binding Tab
Use the **Binding** tab to configure the binding properties specific to the WCF-NetTcp send adapter. The WCF-NetTcp adapter can communicate with a service through the WS-* standards over the TCP transport, using messages that have a binary encoding.  
  
> [!NOTE]
>  The current version of the WCF-NetTcp adapter does not support WS-Reliable Messaging.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Open timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Send timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a send operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**. If you use a solicit-response send port, this value specifies a time span for the whole interaction to complete, even if the service returns a large message.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Close timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Maximum received message size (bytes)**|Specify the maximum size, in bytes, for a message including headers, which can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br /><br /> The WCF-NetTcp adapter leverages the [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) class in the buffered transfer mode to communicate with an endpoint. For the buffered transport mode, the [NetTcpBinding.MaxBufferSize](http://go.microsoft.com/fwlink/?LinkId=81088) property is always equal to the value of this property.<br /><br /> Default value: 65536<br /><br /> Maximum value: 2147483647|  
|**Enable transactions**|Specify whether a message is transmitted to the destination service and deleted from the MessageBox database in a transactional context using the transaction protocol specified in the **Transaction protocol** property.<br /><br /> The default value is cleared.|  
|**Transaction protocol**|Specify the transaction protocol to be used with this binding. Valid values include the following:<br /><br /> -   **OleTransaction**<br />-   **WS-AtomicTransaction**<br /><br /> The default is **OleTransaction**.|  
  
## See Also  
 [How to Configure a WCF-NetTcp Send Port](../core/how-to-configure-a-wcf-nettcp-send-port.md)