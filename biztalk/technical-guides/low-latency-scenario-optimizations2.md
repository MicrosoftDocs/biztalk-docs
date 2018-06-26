---
title: "Low-Latency Scenario Optimizations2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19cd78ce-ad7d-4e4b-8188-a63d707905d5
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Low-Latency Scenario Optimizations
By default, BizTalk Server is optimized for throughput rather than low-latency. The following optimizations can be applied to BizTalk Server in scenarios where reduced latency is required.  
  
> [!NOTE]  
>  These optimizations will improve latency, but may do so at some cost to overall throughput.  
  
## Increase the BizTalk Server host internal message queue size  
 Each BizTalk host has its own internal in-memory queue. Increase the size of this queue from the default value of 100 to 10000 to improve performance for a low-latency scenario. For more information about modifying the value of the internal message queue size, see [How to Modify Resource Based Throttling Settings](http://go.microsoft.com/fwlink/?LinkID=208366) (http://go.microsoft.com/fwlink/?LinkID=208366) in the BizTalk Server documentation.  
  
> [!NOTE]  
>  Increasing the internal message queue size value will increase the memory used by the host instance.  
  
## Increase the BizTalk Server host in-process messages  
 Increase the in-process messages from the default value of 1000 to 10,000 to improve performance. For more information about modifying the value of the in-process messages, see [How to Modify the Default Host Throttling Settings](http://go.microsoft.com/fwlink/?LinkID=208366) (http://go.microsoft.com/fwlink/?LinkID=208366) in the BizTalk Server documentation.  
  
> [!NOTE]  
>  Increasing the internal message queue size value will increase the memory used by the host instance.  
  
## Optimize orchestrations for low latency  
 Follow the recommendations in the “Recommendations for optimizing orchestrations for low latency scenarios” section of [Optimizing Orchestration Performance](../technical-guides/optimizing-orchestration-performance.md).  
  
## Configure polling intervals  
 Use the Settings Dashboard to configure the polling intervals of a given host, across the BizTalk Group. To change Polling Intervals:  
  
1. In the **BizTalk Server Administration Console**, expand **BizTalk Server Administration**, right-click **BizTalk Group**, and then click **Settings**.  
  
2. In the **BizTalk Settings Dashboard** dialog box, on the **Hosts** page, on the **General** tab, under **Polling Intervals**, you will find the **Messaging** and **Orchestration** values. By default, both these values are set to 500 milliseconds.  
  
   The following table lists the polling values that we used for testing on the BizTalk in-process 64-bit Hosts (RxHost, TxHost and PxHost). To disable polling, you can set the polling interval to a very big number as listed in the table.  
  
|Server Hosts|Messaging|Orchestration|  
|------------------|---------------|-------------------|  
|**RxHost**<br /><br /> Because we are only publishing incoming messages to the BizTalk message box through a one-way receive location, polling is not required on the RxHost (receive host).|200000|200000|  
|**TxHost**<br /><br /> Because we are only receiving messaging instances from the BizTalk message box, orchestration polling is not required on the TxHost (send host).|50|200000|  
|**PxHost**<br /><br /> Because we are only receiving orchestration instances from the BizTalk message box, messaging polling is not required on the PxHost (Processing host).|200000|50|  
  
## See Also  
 [Optimizing BizTalk Server Performance](../technical-guides/optimizing-biztalk-server-performance.md)