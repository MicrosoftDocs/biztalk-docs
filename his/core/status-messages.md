---
title: "Status Messages2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2eab58bc-52d1-4d64-aac7-ee8445effb8d
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Status Messages
The local node uses status messages to provide the application with information about the state of its sessions and to give the application control, in association with the host system services control point (SSCP) and primary logical unit (PLU), over the progress of the session. The status messages are designed to allow the application to use all the protocols allowed in the function management (FM) and Transmission Service profiles (TS profiles) supported by the Microsoft® Host Integration Server local node.  
  
 Most applications only need to use a subset of the available status messages. For example, a 3270 device emulator would not require the status messages used in quiesce protocols.  
  
## In This Section  
  
-   [Status-Acknowledge Message](../core/status-acknowledge-message.md)  
  
-   [Status-Control Message](../core/status-control-message.md)  
  
-   [Status-Error Message](../core/status-error-message.md)  
  
-   [Status-Resource Message](../core/status-resource-message.md)  
  
-   [Status-Session Message](../core/status-session-message.md)  
  
-   [Status-RTM Message](../core/status-rtm-message.md)