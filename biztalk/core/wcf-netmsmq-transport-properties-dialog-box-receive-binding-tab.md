---
title: "WCF-NetMsmq Transport Properties Dialog Box, Receive, Binding Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-netmsmq.transport.receive.binding"
helpviewer_keywords: 
  - "WCF-NetMsmq adapters, bindings"
  - "bindings, WCF-NetMsmq adapters"
  - "WCF-NetMsmq adapters, properties"
  - "properties, WCF-NetMsmq adapters"
ms.assetid: 183a2a54-ddde-44b1-891b-76a30eb21146
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-NetMsmq Transport Properties Dialog Box, Receive, Binding Tab
Use the **Binding** tab to define the binding properties specific to the WCF-NetMsmq receive adapter. The WCF-NetMsmq receive adapter can use to communicate with a service through binary-encoded messages over the MSMQ transport. The WCF-NetMsmq adapter provides queued communication in a .NET-to-.NET environment.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Open timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Send timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a send operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Close timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Maximum received message size (bytes)**|Specify the maximum size, in bytes, for a message including headers, which can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br /><br /> Default value: 65536<br /><br /> Maximum value: 2147483647|  
|**Transactional**|Specify the type of message queue: transactional or nontransactional. If this property is selected, each message is delivered only once, and the sender is notified of delivery failures. To send messages through transactional send ports, both the **durable** and **exactlyOnce** binding elements of the client must be set to **true**. If this property is cleared, messages are transferred without delivery assurance. **Note:**  If you use a transactional queue under this receive location, this property must be selected. **Note:**  ReplaceThisText <br /><br /> The default value is selected.|  
|**Ordered processing**|Specify whether to process messages serially. When this property is selected, this receive location accommodates ordered message delivery when used in conjunction with a BizTalk messaging or orchestration send port that has the **Ordered Delivery** option set to **True**. You can select this only when the **Transaction** property is selected.<br /><br /> For more information about the Ordered Delivery option, see the appropriate topics in See Also.<br /><br /> Selecting this property also optimizes resource usage when handling large messages by making the adapter single-threaded. For more information about sending and receiving large messages, see the appropriate topics in See Also.<br /><br /> The default value is cleared.|  
|**Maximum concurrent calls**|Specify the number of concurrent calls to a single service instance. Calls in excess of the limit are queued. Setting this value to 0 is equivalent to setting it to **Int32.MaxValue**.<br /><br /> Default value: 200|  
  
## See Also  
 [How to Configure a WCF-NetMsmq Receive Location](../core/how-to-configure-a-wcf-netmsmq-receive-location.md)   
 [Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md)   
 [Sending and Retrieving Messages within a Transaction](http://go.microsoft.com/fwlink/?LinkID=75752)