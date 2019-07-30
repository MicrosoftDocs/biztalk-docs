---
title: "Status-Acknowledge Message1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a47d910e-644e-49f3-aaba-37844e595aca
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Status-Acknowledge Message
**Status-Acknowledge** messages are the basic mechanism used to enforce inbound and outbound data acknowledgment protocols on all connections. For details about the use of **Status-Acknowledge** messages, see [Outbound Data](../core/outbound-data1.md) and [Inbound Data](../core/inbound-data2.md).  
  
 For a 3270 emulation application, **Status-Acknowledge** messages sent from the application to the local node (acknowledging outbound data from the host) can also carry information about host response times. This allows the local node to maintain response time statistics for sending to the host when required. For details, see [Response Time Monitor Data](../core/response-time-monitor-data1.md).  
  
## See Also  
 [Status-Control Message](../core/status-control-message1.md)   
 [Status-Error Message](../core/status-error-message1.md)   
 [Status-Resource Message](../core/status-resource-message1.md)   
 [Status-Session Message](../core/status-session-message1.md)   
 [Status-RTM Message](../core/status-rtm-message1.md)