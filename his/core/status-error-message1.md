---
description: "Learn more about: Status-Error Message"
title: "Status-Error Message1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Status-Error Message
[Status-Error](./status-error1.md) messages flow from the local node to the application to report request reject and response header (RH) usage error conditions for:  
  
- Errors in outbound expedited data flow control (DFC) requests.  
  
- Errors in outbound session control (SC) requests.  
  
- Errors in inbound responses.  
  
  The **Status-Error** message contains four bytes of error code information that contain the appropriate SNA sense codes for the detected error. For a list of error codes, see [Error and Sense Codes](../core/error-and-sense-codes2.md).  
  
## See Also  
 [Status-Acknowledge Message](../core/status-acknowledge-message1.md)   
 [Status-Control Message](../core/status-control-message1.md)   
 [Status-Resource Message](../core/status-resource-message1.md)   
 [Status-Session Message](../core/status-session-message1.md)   
 [Status-RTM Message](../core/status-rtm-message1.md)
