---
description: "Learn more about: Transaction Size vs. Data Throughput"
title: "Transaction Size vs. Data Throughput2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Transaction Size vs. Data Throughput
As a result of the transaction throughput test shown in [Transaction Size vs. Transaction Throughput](../core/transaction-size-vs-transaction-throughput2.md), the question of what the best message size for these transactions arises. We captured the actual user data transferred with these transactions and looked at the MB/sec throughput versus message size. The following figure shows that if the data throughput is the objective of optimization, the larger the message size, the higher the throughput. Additional considerations can influence the selections of the message size, such as the maximum frame size on the LAN or WAN. For example, Ethernet 802.2 frames can fit 1484 bytes of user data per frame; token-ring can go up to 8186 bytes.  
  
 ![Image that shows a chart displaying megabytes per second on the vertical axis and percent CPU on the horizontal axis.](../core/media/his-ti31.gif "his_ti31")  
Chart displaying megabytes per second on the vertical axis and percent CPU on the horizontal axis  
  
## See Also  
 [Transaction Size vs. Transaction Throughput](../core/transaction-size-vs-transaction-throughput2.md)   
 [Transaction Integrator Performance Guide](../core/transaction-integrator-performance-guide1.md)
