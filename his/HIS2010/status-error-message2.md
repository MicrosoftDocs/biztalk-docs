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
[Status-Error](../HIS2010/status-error2.md) messages flow from the local node to the application to report request reject and response header (RH) usage error conditions for:  
  
-   Errors in outbound expedited data flow control (DFC) requests.  
  
-   Errors in outbound session control (SC) requests.  
  
-   Errors in inbound responses.  
  
 The **Status-Error** message contains four bytes of error code information that contain the appropriate SNA sense codes for the detected error. For a list of error codes, see [Error and Sense Codes](../HIS2010/error-and-sense-codes1.md).  
  
## See Also  
 [Status-Acknowledge Message](../HIS2010/status-acknowledge-message2.md)   
 [Status-Control Message](../HIS2010/status-control-message2.md)   
 [Status-Resource Message](../HIS2010/status-resource-message2.md)   
 [Status-Session Message](../HIS2010/status-session-message2.md)   
 [Status-RTM Message](../HIS2010/status-rtm-message2.md)