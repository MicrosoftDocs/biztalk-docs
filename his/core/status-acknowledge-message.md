---
title: "Status-Acknowledge Message1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a47d910e-644e-49f3-aaba-37844e595aca
caps.latest.revision: 3
---
# Status-Acknowledge Message
**Status-Acknowledge** messages are the basic mechanism used to enforce inbound and outbound data acknowledgment protocols on all connections. For details about the use of **Status-Acknowledge** messages, see [Outbound Data](../core/outbound-data.md) and [Inbound Data](../core/inbound-data.md).  
  
 For a 3270 emulation application, **Status-Acknowledge** messages sent from the application to the local node (acknowledging outbound data from the host) can also carry information about host response times. This allows the local node to maintain response time statistics for sending to the host when required. For details, see [Response Time Monitor Data](../core/response-time-monitor-data.md).  
  
## See Also  
 [Status-Control Message](../core/status-control-message.md)   
 [Status-Error Message](../core/status-error-message.md)   
 [Status-Resource Message](../core/status-resource-message.md)   
 [Status-Session Message](../core/status-session-message.md)   
 [Status-RTM Message](../core/status-rtm-message.md)