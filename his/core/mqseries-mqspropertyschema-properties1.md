---
title: "MQSeries.MQSPropertySchema Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8225e869-60d3-425c-98ad-32937303764e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MQSeries.MQSPropertySchema Properties
The MQSC Adapter exposes the following context properties that are not related to MQSeries Message Descriptor or other MQSeries header structures that can be used in your BizTalk applications. These are part of the MQSeries.dll property schema assembly (MQSeries.MQSPropertySchema) that is deployed in the BizTalk Management database from the server-based MQSeries Adapter. The same property schema is used by the MQSC (client-based) adapter.  
  
|Name|Type|Receive and/or Send|Description|  
|----------|----------|--------------------------|-----------------|  
|CompleteMessage|String|Receive|Set MQSeries to assemble segmented messages or to get the message as is. Use NoAction to read messages from the MQSeries queue without enabling segmentation. Use CompleteMessage to have MQSeries assemble segmented messages before passing them on to the adapter.<br /><br /> Default: No Action<br /><br /> This is not applicable to the MQSC Adapter. Used only for the Server-Based MQSeries Adapter in ‘dynamic receive’ type scenarios.|  
|DataConversion|String|Receive|Character set to which the message should be converted to when retrieving messages from the MQSeries Queue. If this property is set to a value other than ‘None’, the adapter sets the MQGMO CONVERT option when performing an MQGet.<br /><br /> None - Do not convert.<br /><br /> UCS-2 and UTF-16 - Convert to these character sets. MQSeries does not distinguish between them.<br /><br /> UTF-8 - Convert to the UTF-8 character set.<br /><br /> Default: None|  
|Ordered|String|Receive|Specify Yes to maintain the order of the messages as they are received from the MQSeries queue and submitted to the BizTalk Server Message Box.<br /><br /> For the send side, the adapter sends the message to the queue in the same order that it receives it from the message box.<br /><br /> Specify No to not maintain message order.<br /><br /> Note – For send side ordering, if you are not using Orchestration, you must enable ‘Ordered Delivery’ in the ‘Transport Advanced Options’ in the send port configuration.<br /><br /> Note – For receive, if you are using Orchestration, you must also set the Ordered Delivery property to True in your orchestration for this receive location.<br /><br /> Note – If ordering is enabled, the adapter switches to single-thread mode and uses synchronous-mode delivery of messages into BizTalk Server. This results in performance degradation, so unless you require ordered delivery, it is not recommended to enable this feature.<br /><br /> Default: No|  
|SegmentationAllowed|String|Send|Set this to Yes to tell MQSeries Queue Manager to create segmented messages when submitting large messages to MQSeries Queues.<br /><br /> Default: No|  
|SSOAffiliateApplication|String|Send|Sets the Single Sign-On (SSO) Affiliate Application name. You use the user ID and password from SSO for the MQMD_UserIdentifier, and the MQIIH_Authenticator (or MQCIH_Authenticator) property respectively.<br /><br /> Default: Blank|  
|WaitInterval|Int|Receive|When performing MQGet, specify the Wait Interval MQGMO option in seconds by setting this property. If there are no messages in the queue, the client will continue waiting for messages in the Queue without closing the connection.<br /><br /> Unit – Seconds<br /><br /> Default – 3|  
|TransactionSupported|String|Receive and Send|When set to Yes, the adapter begins a Microsoft Distributed Transaction Coordinator (DTC) transaction between BizTalk Server and MQSeries. This guarantees once and only once delivery of messages and prevents loss of messages.<br /><br /> Setting this option to Yes means that WebSphere MQ Extended Transactional Client (Extended-Client) is used on the BizTalk Server computer by the adapter.<br /><br /> When set to No, there could be message duplication. In this case, the adapter uses the non-transactional WebSphere MQ Client (Base-Client) for integration with MQSeries.<br /><br /> Default: Yes|