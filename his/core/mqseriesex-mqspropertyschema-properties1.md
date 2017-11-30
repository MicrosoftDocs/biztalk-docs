---
title: "MQSeriesEx.MQSPropertySchema Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6954786-ad65-4538-8904-4fb3edcb0cd1
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MQSeriesEx.MQSPropertySchema Properties
This contains additional context properties that are applicable only to the MQSC adapter (client-based MQSeries Adapter) for receive location and send port configurations. They are not applicable to the server-based adapter. These properties are associated with the channel configuration.  
  
|Name|Type|Receive and/or Send|Description|  
|----------|----------|--------------------------|-----------------|  
|Channel_HeartBeat|unsignedInt|Receive and Send|The time between checks to verify if the client-server connection is working.<br /><br /> Unit – Seconds<br /><br /> Default - 300|  
|Channel_UserId|String|Receive and Send|Set MQSeries to assemble segmented messages or to get the message as is. Use NoAction to read messages from the MQSeries queue without enabling segmentation. Use CompleteMessage to have MQSeries assemble segmented messages before passing them on to the adapter.<br /><br /> Default: NoAction|  
|Channel_Password|String|Receive and Send|The password may be used by the MCA when attempting to initiate a secure LU 6.2 session with a remote MCA.<br /><br /> The initial value is null. This is an optional property.|  
|Channel_SslCipherSpecification|String|Receive and Send|This defines a single CipherSpec for an SSL connection that will be used by the end-point configured in the adapter. Both ends of a WebSphere MQ SSL channel definition must include the attribute and the value specified here should match the name specified on the server end of the channel. The value is a string with a maximum length of 32 characters.<br /><br /> This is required only when SSL is configured for the MQSeries Client to remote Queue Managers communication.|  
|Channel_SslClientAuthentication|String|Receive and Send|This property determines whether the channel needs to receive and authenticate an SSL certificate from an SSL client. This is Optional by default. If two-way authentication (client/server) is required, this property should be set to Required. Before doing this, you must have configured SSL in MQSeries to enable client/server authentication so that the SSL client can send a valid certificate for authentication to succeed.<br /><br /> Default: Optional|  
|Channel_SslPeerName|String|Receive and Send|The property is used to check the Distinguished Name (DN) of the certificate from the peer queue manager or client at the other end of a WebSphere MQ channel. If the DN received from the peer does not match this value, the channel does not start.<br /><br /> This is required only when SSL is configured for the MQSeries Client to Queue Managers communication.|