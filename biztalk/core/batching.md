---
description: "Learn more about: Batching"
title: "Batching"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Batching
*Batching* is a serialized processing of a set of messages that allows for optimizations with respect to database round trips. A batch is a unit of work that is atomic; that is, it either all succeeds or all fails. If one operation in a batch succeeds but another operation fails, all the operations that make up the batch are invalidated and must be repeated.  
  
 BizTalk Server uses batching to:  
  
-   Amortize the cost of the transaction across many messages.  
  
-   Increase speed by reducing the internal number of database round trips.  
  
-   Make more efficient use of the BizTalk Server thread pool by using the BizTalk Server Asynchronous API.  
  
## Applying Batching  
 Batching is configured in the advanced properties for a receive location and is enabled automatically on the send port side.  
  
## Lowering the Batch Size  
 You should lower the batch size if in the following instances:  
  
-   When processing large messages  
  
-   When database round trips are not your bottleneck  
  
> [!NOTE]
>  Be careful when changing the **LargeMessageThreshold** setting. The batch size multiplied by the average message size should be less than the **LargeMessageThreshold** setting unless the batch size is 1.  
  
## See Also  
 [The Messaging Engine](../core/the-messaging-engine.md)   
 [Batching Messages for Receive Processing](../core/batching-messages-for-receive-processing.md)   
 [Batching Messages for Send Processing](../core/batching-messages-for-send-processing.md)
