---
description: "Learn more about: How to Manage Multiple Receive Locations Using the MSMQ Adapter"
title: "How to Manage Multiple Receive Locations Using the MSMQ Adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Manage Multiple Receive Locations Using the MSMQ Adapter
To increase performance, the MSMQ adapter is multithreaded. If you have many receive locations, there may not be enough threads available for all the receive locations. This prevents some of the receive locations from picking up messages. There are three ways to solve this problem:  
  
-   Add BizTalk Hosts to your computer and divide the receive locations among the hosts. Adding hosts makes more threads available for the receive locations.  
  
-   Set the **Serial Processing** property to `True` on each receive location. Setting the property to `True` assigns a single thread to each receive location. This leaves more threads available in the pool. However, this may also cause a decrease in performance.  
  
-   Modify the registry to increase the number of threads that are available to the host for the MSMQ adapter receive handler. For more information see the **Modify the CLR Hosting thread values for the host** section of [Configuration Parameters that Affect Adapter Performance](../core/configuration-parameters-that-affect-adapter-performance.md).  
  
## See Also  
 [Configuring the MSMQ Adapter](../core/configuring-the-msmq-adapter.md)
