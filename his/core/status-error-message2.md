---
title: "Status-Error Message2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1762b870-6826-491f-99dc-e8782b26741a
caps.latest.revision: 3
---
# Status-Error Message
[Status-Error](../core/status-error2.md) messages flow from the local node to the application to report request reject and response header (RH) usage error conditions for:  
  
-   Errors in outbound expedited data flow control (DFC) requests.  
  
-   Errors in outbound session control (SC) requests.  
  
-   Errors in inbound responses.  
  
 The **Status-Error** message contains four bytes of error code information that contain the appropriate SNA sense codes for the detected error. For a list of error codes, see [Error and Sense Codes](../core/error-and-sense-codes1.md).  
  
## See Also  
 [Status-Acknowledge Message](../core/status-acknowledge-message2.md)   
 [Status-Control Message](../core/status-control-message2.md)   
 [Status-Resource Message](../core/status-resource-message2.md)   
 [Status-Session Message](../core/status-session-message2.md)   
 [Status-RTM Message](../core/status-rtm-message2.md)