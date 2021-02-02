---
description: "Learn more about: Properties Related to BizTalk Server"
title: "Properties Related to BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [MQSeries adapters], properties"
  - "CompleteMessage property [MQSeries adapters]"
  - "SSOAffiliateApplication property [MQSeries adapters]"
  - "Ordered property [MQSeries adapters]"
  - "TransactionSupported property [MQSeries adapters]"
  - "BizTalk_CorrelationID property [MQSeries adapters]"
  - "SegmentationAllowed property [MQSeries adapters]"
  - "DynamicReceive property [MQSeries adapters]"
  - "MQSeries adapters, properties"
  - "DataConversion property [MQSeries adapters]"
ms.assetid: c27d7f9c-8198-4624-9952-054ba8ea1c7c
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Properties Related to BizTalk Server
The MQSeries adapter assigns values to some context properties that are not directly related to MQSeries but are still useful in your applications.  
  
 All the properties receive values during sending and receiving except for **BizTalk_CorrelationID**. The **BizTalk_CorrelationID** property has a value only during receiving.  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|**BizTalk_CorrelationID**|string|Use this property to have the MQSeries server generate a correlation identifier for use with the message.<br /><br /> For more information, see [Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md).|  
|**DataConversion**|string|Converts the message to the ANSI code page of MQSeries Server for Windows. On Send, if the message format is not MQFMT_STRING, there is no conversion.<br /><br /> Select **Yes** to perform this conversion from Unicode to ANSI.<br /><br /> **Default:** No|  
|**Ordered**|string|Sets MQSeries to maintain the order of the messages as they are received from or sent to the MQSeries queue.<br /><br /> The property has different sets of values for sending and receiving. For information about the values, see. [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).<br /><br /> **Default:** No|  
|**SegmentationAllowed**|string|Sets MQSeries to assemble segmented messages or to get the message as is. The property has different sets of values for sending and receiving.<br /><br /> When receiving, use **No Action** to read messages from the MQSeries queue without enabling segmentation; use **Complete Message** to have MQSeries assemble segmented messages before passing them on to the adapter.<br /><br /> **Default:** No Action<br /><br /> When sending, select **Yes**, to have MQSeries put segmented messages in the queue.<br /><br /> **Default:** No|  
|**SSOAffiliateApplication**|string|Sets the Single Sign-On (SSO) affiliate application. You use the user ID and password from SSO for the **MQMD_UserIdentifier**, and the **MQIIH_Authenticator** (or **MQCIH_Authenticator**) property respectively.<br /><br /> Used only when sending messages.<br /><br /> **Default:** Blank|  
|**CompleteMessage**|string|Designates whether to retrieve "complete message" when retrieving segmented messages from a queue.<br /><br /> Set this to **Yes** to retrieve the "complete message" for segmented messages in a queue.<br /><br /> **Default:** No|  
|**DynamicReceive**|string|Designates whether to receive messages from a queue dynamically.<br /><br /> Set this to **Yes** when receiving messages from a queue dynamically. This feature is used in conjunction with a solicit-response send port.<br /><br /> If you specify match options (MessageID, CorrelationID, or GroupID), then only messages that correlate to the match criteria will be retrieved.|  
|**TransactionSupported**|string|The adapter begins a Microsoft Distributed Transaction Coordinator (DTC) transaction between BizTalk Server and MQSeries Server. When set to **No**, there is no guarantee of message delivery.<br /><br /> **Default:** Yes|  
|**WaitInterval**|string|Specifies the approximate time, expressed in seconds, that the MQ system waits for a suitable message to arrive. If no suitable message has arrived in this time, the call fails. **Note:**  This can be set within an orchestration only. <br /><br /> **Default:** 3|  
  
## See Also  
 [MQSeries Adapter Properties](../core/mqseries-adapter-properties.md)   
 [Data Type Conversion of Properties](../core/data-type-conversion-of-properties.md)   
 [MQSeries Context Properties](../core/mqseries-context-properties.md)
