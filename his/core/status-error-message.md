---
title: "Status-Error Message1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9c3a7c8-26b3-44e9-a2a1-9a1039e6dfd0
caps.latest.revision: 3
---
# Status-Error Message
[Status-Error](../Topic/Status-Error2.md) messages flow from the local node to the application to report request reject and response header (RH) usage error conditions for:  
  
-   Errors in outbound expedited data flow control (DFC) requests.  
  
-   Errors in outbound session control (SC) requests.  
  
-   Errors in inbound responses.  
  
 The **Status-Error** message contains four bytes of error code information that contain the appropriate SNA sense codes for the detected error. For a list of error codes, see [Error and Sense Codes](../core/error-and-sense-codes.md).  
  
## See Also  
 [Status-Acknowledge Message](../core/status-acknowledge-message.md)   
 [Status-Control Message](../core/status-control-message.md)   
 [Status-Resource Message](../core/status-resource-message.md)   
 [Status-Session Message](../core/status-session-message.md)   
 [Status-RTM Message](../core/status-rtm-message.md)