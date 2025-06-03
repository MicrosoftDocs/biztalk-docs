---
title: "Enable fault tolerance in receive locations"
description: Use fault tolerance to help make BizTalk Server receive locations highly available. Keep processing messages, even when an error occurs.
ms.date: "05/20/2022"
ms.topic: how-to
ms.service: biztalk-server
# optional metadata
#ROBOTS:
ms.reviewer: 
ms.suite:
ms.custom:
   - "biztalk-2020"
   - kr2b-contr-experiment
---
# Enable fault tolerance in BizTalk Server receive locations

You can use fault tolerance to help make your BizTalk Server receive locations highly available (HA).

## Create an HA environment

To set up an HA environment, you can create two or more instances for each receiving host. In an HA environment, receive workloads are distributed between different host instances.

For example, you create three host instances: A, B, and C. These instances run your HTTP receive location. You also use a network load balancer (NLB) to distribute the receiving workload across these host instances.

The HTTP receive adapter might fail in host instance A, perhaps due to a disk-full error. In the past, this situation could make the entire receive location unavailable. Host instances B and C would also stop receiving messages, even though these host instances didn't have any issues.

**BizTalk Server 2020 and later versions** offer fault tolerance. You can configure receive locations to recover from transient errors instead of becoming unavailable. When an error occurs, receive locations go down in the host instance with the error. But the receive location continues to run in the other host instances. BizTalk attempts to recover the unavailable receive location. You can specify how often it attempts a retry.

## Turn on fault tolerance

1. Open the BizTalk Server Administration console.
1. Right-click the **BizTalk Group**, and then select **Settings**.
1. In the **BizTalk Settings Dashboard** dialog, select **Group**.
1. Select **Enable fault tolerance**.
1. In the **Retry interval** box, enter the number of seconds for BizTalk to wait between attempts to recover receive locations. By default, BizTalk attempts a retry every 60 seconds.
1. Select **OK** to save your changes.

## Next steps

[Configure a receive location schedule in BizTalk Server](../core/how-to-configure-scheduling-for-a-receive-location.md)
