---
title: "Status-Resource Message2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 26d38ffb-d960-45a8-9e06-be92989444a2
caps.latest.revision: 3
---
# Status-Resource Message
[Status-Resource](../HIS2010/status-resource2.md) messages flow between an application and the local node to enable the local node to pace the primary logical unit (PLU) session of the application. They provide the local node with an indication of the buffer resources available at the application to receive outbound messages. With this information, the local node can determine when to send a pacing response. (For more information, see [Pacing and Chunking](../HIS2010/pacing-and-chunking2.md).)  
  
> [!NOTE]
>  Flow control is an option. Inbound pacing is handled by the local node, transparently to the application, and outbound pacing can be handled similarly. This is appropriate when only a limited number of messages flows from end-to-end of the SNA session between definite responses, such as with a 3270 screen.  
  
## See Also  
 [Status-Acknowledge Message](../HIS2010/status-acknowledge-message2.md)   
 [Status-Control Message](../HIS2010/status-control-message2.md)   
 [Status-Error Message](../HIS2010/status-error-message2.md)   
 [Status-Session Message](../HIS2010/status-session-message2.md)   
 [Status-RTM Message](../HIS2010/status-rtm-message2.md)