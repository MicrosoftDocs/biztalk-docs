---
title: "MQSeries Transport Properties Dialog Box, Receive | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.mqseries.transport.receive"
helpviewer_keywords: 
  - "properties, MQSeries adapters"
  - "MQSeries adapters, properties"
  - "MQSeries adapters, receive locations"
  - "receive locations, MQSeries adapters"
ms.assetid: 9518d873-f0f7-41e3-adbe-75f6be97a23a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MQSeries Transport Properties Dialog Box, Receive
Use the **MQSeries Transport Properties** dialog box to configure the receive location properties for the MQSeries adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Event Log Error Threshold**|Determine the maximum number of errors to log. The adapter continues operating and, if the adapter recovers, it logs the event in the event log.|  
|**Fragmentation Size**|Set the message chunk size in KB for messages as they are sent between MQSAgent and the adapter.|  
|**Maximum Batch Size**|Determine the maximum size of a batch of messages in KB. **Note:**  If the **Transaction Supported** property for the receive location is set to **Yes**; each message batch is submitted to the MessageBox database under the context of a Microsoft Distributed Transaction Coordinator (MSDTC) transaction. The MSDTC transaction that is created for a message batch remains open until every message in the batch has been persisted to the MessageBox and placed in the appropriate subscriber queue. Therefore the duration of this MSDTC transaction is increased as the **Maximum Batch Size** parameter is increased. Since having a large number of MSDTC transactions open simultaneously can negatively impact overall performance, the **Maximum Batch Size** parameter should not be set to a very large value when transaction support is enabled.|  
|**Maximum Messages in Batch**|The maximum number of messages from 1 through 10,000 in a batch.|  
|**Polling Interval**|Set the time interval from 0 to infinity used by the receive component to poll the MQSeries queue.<br /><br /> The Polling Interval works in combination with the hard-coded wait interval of three seconds built into the adapter. If the Polling Interval value is less than 3 seconds, the wait interval is set to the value of the Polling Interval.|  
|**Polling Unit**|Set the unit of time for the polling interval.<br /><br /> Default: Seconds|  
|**Threads**|Establish the number of threads used per receive location.|  
|**Character Set**|Determine the character set and whether MQSeries converts characters before sending the message to the receive location:<br /><br /> -   None. Do not convert. UCS-2 and UTF-16. Convert to these character sets. MQSeries does not distinguish between them.<br />-   UTF-8. Convert to the UTF-8 character set.<br /><br /> Default: None|  
|**Data Offset for Headers**|The adapter uses values from the MQSeries headers (the MQXQH, MQIIH, and MQCIH structures) to populate corresponding values in the BizTalk Server context properties. By default, the adapter removes these MQSeries properties from the message body. Set this property to No to retain the properties in the message body.<br /><br /> Default: Yes|  
|**Ordered**|Set MQSeries to maintain the order of the messages as they are received from the MQSeries queue.<br /><br /> Select No Ordering to disregard message order.<br /><br /> Select No Ordering with stop to disregard message order and to disable the receive location if there is an error.<br /><br /> Use Order with Stop to enable ordering. This option ends the transaction and disables the receive location if there is an error.<br /><br /> Use Order with Suspend to enable ordering. This option moves the message to the suspended queue when there is an error. This value does not preserve order when there is an error, but does allow the receive location to continue receiving messages. **Note:**  To maintain message ordering for a specific queue, only one BizTalk Server host instance may be receiving messages from that MQSeries queue. **Note:**  You must also set the Ordered Delivery property to True in your orchestration for this receive location. **Note:**  Enabling ordered delivery will accommodate ordered message delivery when used in conjunction with a BizTalk Messaging or Orchestration Send Port that has the Ordered Delivery option set to True. For more information about the Ordered Delivery option, see the appropriate topics under See Also. <br /><br /> Default: No Ordering|  
|**Queue Definition**|Filled in with information from the Queue Definition dialog box.|  
|**Segmentation**|Set MQSeries to assemble segmented messages or to get the message as is. Use No Action to read messages from the MQSeries queue without enabling segmentation. Use Complete Message to have MQSeries assemble segmented messages before passing them on to the adapter.<br /><br /> Default: No Action|  
|**Suspend As Non Resumable**|Specify whether suspended messages are marked as resumable or not.<br /><br /> Default: No|  
|**Transaction Supported**|The adapter begins a Distributed Transaction Coordinator (DTC) transaction between BizTalk Server and MQSeries server. When set to No, there is no guarantee of message delivery.<br /><br /> Default: Yes|  
  
## See Also  
 [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)   
 [Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md)