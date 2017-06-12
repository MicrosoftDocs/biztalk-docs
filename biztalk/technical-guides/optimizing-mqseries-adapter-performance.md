---
title: "Optimizing MQSeries Adapter Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a46455c-a8d2-4427-99bb-4e3c6dbd9566
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Optimizing MQSeries Adapter Performance
Configure the MQSeries adapter by using the following settings when possible to increase performance.  
  
## Adjust the value for the MQSeries receive adapter polling threads  
 Increase the value specified for **Threads** in the **MQSeries Transport Properties** when configuring MQSeries adapter receive locations. Increasing this property from the default value of 2 to a value of 5 will significantly improve the rate at which messages can be received using the MQSeries adapter.  
  
## Disable transaction support on MQSeries receive locations where not required  
 MQSeries adapter transaction support incurs significant overhead. If transaction support is not a business requirement, set the **Transaction Supported** value in the **MQSeries Transport Properties** dialog box from the default value of **Yes** to **No**.  
  
## Disable Ordered delivery of messages on the MQSeries Adapter when not required  
 Enabling this property will enforce ordered delivery of messages as they are received from or sent to the MQSeries queue but will affect performance. When ordered delivery is enabled, the messaging runtime will use a single thread to receive messages from a given MQSeries queue. If ordered delivery of messages is not a business requirement, then do not change the default value of **Ordered** property in the **MQSeries Transport Properties** dialog box which is set as **No Ordering**.  
  
## See Also  
 [Optimizing BizTalk Server Performance](../technical-guides/optimizing-biztalk-server-performance.md)