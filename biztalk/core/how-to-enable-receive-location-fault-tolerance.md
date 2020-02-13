---
title: "How to Enable Receive Location fault tolerance  | Microsoft Docs"
description: How to Enable Receive Location Fault Tolerance.
author: "pravagar"
ms.author: "pravagar"
manager: "dougeby"
ms.date: "02/13/2020"
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

To make your environment highly available, you can create two or more host instances for each receiving host. In such environment, receive workloads will be distributed between different host instances. For example, you can use a Network Load Balancer (NLB), to distribute receiving workload for HTTP adapter. But if a receive adapter encounters error in one host instance, it may completely disable the receive location and other host instances running the receive adapter will stop processing incoming workloads. For example, you can create three host instances (A, B and C) to run HTTP receive adapter. If HTTP receive adapter fails in host instance A, say, due to disk full error, it can completely disable the receive location. Host instance B and C will stop receiving message though these hosts have no issues.

**Starting with BizTalk Server 2020 and newer**, you can configure receive locations to recover from transient errors instead of getting completely disabled. On error, receive locations will be disabled in the host instance where it is faulted and BizTalk will attempt to recover it in certain configurable interval. The receive location will continue running in other host instances.

## Configuring fault tolerance behavior

1. In the **BizTalk Server Administration** console, right-click the **BizTalk Group**, and select **Settings**.
2. In the **BizTalk Settings Dashboard** dialog box, select the **Group** page.

3. Check **Enable fault tolerance**.

4. Set **Retry interval** to desired number. By default, BizTalk attempts to recover receive locations from fault in 60 seconds interval.

5. Select **OK** to save your changes.
