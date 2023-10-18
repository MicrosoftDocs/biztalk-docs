---
description: "Learn more about: MQSeries Adapter High Availability"
title: "MQSeries Adapter High Availability"
ms.custom: "devx-track-javaee-websphere"
ms.date: "12/30/2022"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MQSeries Adapter High Availability
You can improve availability in the following ways when you use the adapter:

- Set up a fault-tolerant hosting environment for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].

- Use Windows Clustering with IBM WebSphere MQ.

  For information about fault tolerance and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md) and [Planning Your Platform for Fault Tolerance](../core/planning-your-platform-for-fault-tolerance.md) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.

  To ensure that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries Adapter is able to communicate with a remote installation of the MQSAgent component, ensure that you have enabled network COM+ access on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]and server where IBM WebSphere MQ is installed. For more information about enabling network COM+ access, see [Network Access](/windows/win32/cossdk/what-s-new-in-com--1-5#network-access).

  There is no requirement to cluster the MQSAgent (MQSAgent2) COM+ application that is used with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries adapter. To provide high availability for this component, install the component on each cluster node. If the COM+ application stops, the next call from the client will start it.

## See Also
 [Using the MQSeries Adapter](../core/using-the-mqseries-adapter.md)
