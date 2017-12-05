---
title: "Status Messages1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b18c710-47e5-470f-a582-548863c57c7b
caps.latest.revision: 3
---
# Status Messages
The local node uses status messages to provide the application with information about the state of its sessions and to give the application control, in association with the host system services control point (SSCP) and primary logical unit (PLU), over the progress of the session. The status messages are designed to allow the application to use all the protocols allowed in the function management (FM) and Transmission Service profiles (TS profiles) supported by the Microsoft® Host Integration Server local node.  
  
 Most applications only need to use a subset of the available status messages. For example, a 3270 device emulator would not require the status messages used in quiesce protocols.  
  
## In This Section  
  
-   [Status-Acknowledge Message](../core/status-acknowledge-message2.md)  
  
-   [Status-Control Message](../core/status-control-message2.md)  
  
-   [Status-Error Message](../core/status-error-message2.md)  
  
-   [Status-Resource Message](../core/status-resource-message2.md)  
  
-   [Status-Session Message](../core/status-session-message2.md)  
  
-   [Status-RTM Message](../core/status-rtm-message2.md)