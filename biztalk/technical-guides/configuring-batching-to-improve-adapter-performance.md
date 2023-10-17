---
description: "Learn more about: Configuring Batching to Improve Adapter Performance"
title: "Configuring Batching to Improve Adapter Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65589925-af94-45f1-b501-37c21618b2cf
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Batching to Improve Adapter Performance
The way an adapter processes a batch can have a significant effect on performance. Because there is a fixed delay associated with each transaction, you should try to minimize the number of transactions by combining more than one operation into a single batch.  
  
 If you are submitting messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in batches, do not limit the batch size based only on the message count. For example, if the batch size is two and the adapter gets four messages of size 4 KB, 8 KB, 1 MB, and 5 MB respectively, the first batch will be of size 12 KB, and the second batch will be of size 6 MB. Because the BizTalk Messaging Engine processes all messages in a single batch sequentially, the second batch in this example will be processed much more slowly than the first batch. The effect of this is reduced throughput.  
  
 To handle this problem, we recommend that you batch based on both the message count and the total number of bytes in the batch (that is, batch size in bytes). There is no optimal number for total bytes. However, in a normal processing scenario, if the batch size exceeds 1 MB, you will start encountering poor concurrency and throughput.  
  
 Adapters generally process messages of varying size in the production environment. The sizes of incoming messages are likely to vary significantly. As a result, always use message count and total bytes to build the batch.
