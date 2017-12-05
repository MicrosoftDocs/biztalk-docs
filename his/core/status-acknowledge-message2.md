---
title: "Status-Acknowledge Message2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13061482-a347-4b45-be5e-63264a5d6495
caps.latest.revision: 3
---
# Status-Acknowledge Message
**Status-Acknowledge** messages are the basic mechanism used to enforce inbound and outbound data acknowledgment protocols on all connections. For details about the use of **Status-Acknowledge** messages, see [Outbound Data](../core/outbound-data2.md) and [Inbound Data](../core/inbound-data1.md).  
  
 For a 3270 emulation application, **Status-Acknowledge** messages sent from the application to the local node (acknowledging outbound data from the host) can also carry information about host response times. This allows the local node to maintain response time statistics for sending to the host when required. For details, see [Response Time Monitor Data](../core/response-time-monitor-data2.md).  
  
## See Also  
 [Status-Control Message](../core/status-control-message2.md)   
 [Status-Error Message](../core/status-error-message2.md)   
 [Status-Resource Message](../core/status-resource-message2.md)   
 [Status-Session Message](../core/status-session-message2.md)   
 [Status-RTM Message](../core/status-rtm-message2.md)