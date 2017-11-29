---
title: "Status-Resource Message1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e00aa42b-3715-4e00-9bd9-cbfb8b899c28
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Status-Resource Message
[Status-Resource](../Topic/Status-Resource2.md) messages flow between an application and the local node to enable the local node to pace the primary logical unit (PLU) session of the application. They provide the local node with an indication of the buffer resources available at the application to receive outbound messages. With this information, the local node can determine when to send a pacing response. (For more information, see [Pacing and Chunking](../core/pacing-and-chunking.md).)  
  
> [!NOTE]
>  Flow control is an option. Inbound pacing is handled by the local node, transparently to the application, and outbound pacing can be handled similarly. This is appropriate when only a limited number of messages flows from end-to-end of the SNA session between definite responses, such as with a 3270 screen.  
  
## See Also  
 [Status-Acknowledge Message](../core/status-acknowledge-message.md)   
 [Status-Control Message](../core/status-control-message.md)   
 [Status-Error Message](../core/status-error-message.md)   
 [Status-Session Message](../core/status-session-message.md)   
 [Status-RTM Message](../core/status-rtm-message.md)