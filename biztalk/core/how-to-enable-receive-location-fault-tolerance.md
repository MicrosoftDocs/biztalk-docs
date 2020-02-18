---
title: "Enable Receive Location fault tolerance  | Microsoft Docs"
description: Enable fault tolerance on receive locations to keep processing messages, even when an error occurs.
author: "pravagar"
ms.author: "pravagar"
manager: "dougeby"
ms.date: "02/18/2020"
ms.topic: conceptual
ms.prod: biztalk-server

# optional metadata

#ROBOTS:

ms.reviewer: 
ms.suite:
ms.tgt_pltfrm:
ms.assetid: 
ms.custom: "biztalk-2020"

---
# How to Enable Receive Location Fault Tolerance

## Overview

To make your environment highly available (HA), you can create two or more host instances for each receiving host. In a HA environment, receive workloads are distributed between different host instances.

For example, you create three host instances (A, B anc C) to run your HTTP receive location. You also use a Network Load Balancer (NLB) to distribute the receiving workload across these host instances. If the HTTP receive adapter fails in host instance A, such as a disk full error, it can completely disable the receive location. Host instances B and C also stop receiving messages, even though these host instances don't have any issues.

**Starting with BizTalk Server 2020 and newer**, you can configure receive locations to recover from transient errors, instead of getting disabled. On error, receive locations are disabled in the specific host instance. BizTalk attempts to recover the receive location in an interval you set. The receive location continues running in the other host instances.

## Turn on fault tolerance

1. In the **BizTalk Server Administration** console, right-click the **BizTalk Group**, and select **Settings**.
2. In the **BizTalk Settings Dashboard** dialog box, select the **Group** page.
3. Check **Enable fault tolerance**.
4. Set **Retry interval** to desired number. By default, BizTalk attempts to recover receive locations from fault in 60 seconds interval.
5. Select **OK** to save your changes.

## Next steps

[Configure scheduling](core/how-to-configure-scheduling-for-a-receive-location.md) on your receive location.
