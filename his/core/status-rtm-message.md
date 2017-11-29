---
title: "Status-RTM Message1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc20b5aa-01bc-4524-b00a-d5b776d64928
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Status-RTM Message
The [Status-RTM](../Topic/Status-RTM2.md) message is used by the local node to inform the application of the Response Time Monitor (RTM) parameters being used by the host. It flows from the local node to the application on the system services control point (SSCP) connection and is sent only for 3270 display logical units (LUs), or LUs in a pool of display LUs.  
  
 The **Status-RTM** message is sent at the following times:  
  
-   After the OK response to the [Open(SSCP) Request](../Topic/Open\(SSCP\)%20Request1.md) message, to inform the application of the initial RTM parameters.  
  
-   When the RTM counters are reset, either due to a request from the host or when the local node sends unsolicited RTM data to the host.  
  
-   When any of the RTM parameters are changed by the host.  
  
 For more information about the use of the **Status-RTM** message, see [RTM Parameters](../core/rtm-parameters].md). For more information about how the application supplies RTM data to the local node, see [Response Time Monitor Data](../core/response-time-monitor-data.md).  
  
## See Also  
 [Status-Acknowledge Message](../core/status-acknowledge-message.md)   
 [Status-Control Message](../core/status-control-message.md)   
 [Status-Error Message](../core/status-error-message.md)   
 [Status-Resource Message](../core/status-resource-message.md)   
 [Status-Session Message](../core/status-session-message.md)