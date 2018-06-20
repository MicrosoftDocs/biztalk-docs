---
title: "Message Batches | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5f893d16-2670-4463-9a89-6f5be912a045
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Batches
When your adapter has a group of messages that need to be processed at one time, you should batch these messages to optimize performance. Programmatically, message batches are collections of messages with an associated operation. By grouping messages in a batch rather than submitting each message individually, you optimize the use of resources and processing tasks. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses batching to:  

- Amortize the cost of the transaction across many messages.  

- Increase speed by reducing the internal number of database round trips.  

- Make more efficient use of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] thread pool by processing the messages asynchronously.  

  A batch is a unit of work that is atomic. That is, either all operations in it succeed or all operations in it fail. If one operation in a batch succeeds but another operation fails, all the operations that make up the batch are invalidated and the messages must be resubmitted. This means that an adapter must do three things in response to a failed batch:  

- Determine which messages failed.  

- Decide what to do with the failed messages.  

- Resubmit the messages that did not fail.
