---
description: "Learn more about: Ordered Delivery of Messages with the MSMQ Adapter"
title: "Ordered Delivery of Messages with the MSMQ Adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Ordered Delivery of Messages with the MSMQ Adapter
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides an **Ordered Delivery** option for static send ports. Setting the **Ordered Delivery** option on a send port to **True** ensures that BizTalk Server delivers messages to the send port in the same order that they are published to the MessageBox database. To provide end-to-end ordered delivery the following conditions must be met:  
  
-   Messages must be received with an adapter that preserves the order of the messages when submitting them to BizTalk Server.  
  
-   You must subscribe to these messages with a send port that has the **Ordered Delivery** option to **True**.  
  
-   If an orchestration is used to process the messages, only a single instance of the orchestration should be used, the orchestration should be configured to use a sequential convoy, and the **Ordered Delivery** property of the orchestration's receive port should be set to **True**.  
  
## Using the MSMQ Adapter for Ordered Delivery of Messages  
 The MSMQ receive adapter provides support for preserving the order of messages when submitting them to BizTalk Server. End-to-end ordered delivery of messages through BizTalk Server can be achieved when receiving messages with the MSMQ adapter if the messages are processed by a send port that is configured with the **Ordered Delivery** option set to **True**.  
  
## See Also  
 [Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md)   
 [How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md)
