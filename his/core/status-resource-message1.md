---
description: "Learn more about: Status-Resource Message"
title: "Status-Resource Message1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Status-Resource Message
[Status-Resource](./status-resource1.md) messages flow between an application and the local node to enable the local node to pace the primary logical unit (PLU) session of the application. They provide the local node with an indication of the buffer resources available at the application to receive outbound messages. With this information, the local node can determine when to send a pacing response. (For more information, see [Pacing and Chunking](../core/pacing-and-chunking1.md).)  
  
> [!NOTE]
>  Flow control is an option. Inbound pacing is handled by the local node, transparently to the application, and outbound pacing can be handled similarly. This is appropriate when only a limited number of messages flows from end-to-end of the SNA session between definite responses, such as with a 3270 screen.  
  
## See Also  
 [Status-Acknowledge Message](../core/status-acknowledge-message1.md)   
 [Status-Control Message](../core/status-control-message1.md)   
 [Status-Error Message](../core/status-error-message1.md)   
 [Status-Session Message](../core/status-session-message1.md)   
 [Status-RTM Message](../core/status-rtm-message1.md)
