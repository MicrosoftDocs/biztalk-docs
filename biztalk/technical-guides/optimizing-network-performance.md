---
description: "Learn more about: Optimizing Network Performance"
title: "Optimizing Network Performance"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Optimizing Network Performance
In a BizTalk Server environment where the BizTalk Server computer is separate from the SQL Server computer, each and every message processed by BizTalk Server requires communication over the network. This communication includes considerable traffic between the BizTalk Server computer and the BizTalk MessageBox database, the BizTalk Management database, the BAM databases, and other databases. In high-load scenarios, this communication can result in considerable network traffic and can become a bottleneck, especially when network settings have not been optimized, not enough network interface cards are installed, or insufficient network bandwidth is available.

 This section provides some general recommendations for improving network performance and describes several registry entries that can be modified to optimize the network stack to mitigate the occurrence of bottlenecks on the network.

> [!IMPORTANT]
>  Some of the recommendations in this section require modifications to the Windows registry. Incorrect use of Registry Editor may cause problems requiring you to reinstall your operating system. Use Registry Editor at your own risk. For more information about how to back up, restore, and modify the registry, see the Microsoft Knowledge Base article [256896, "Windows registry information for advanced users"](/troubleshoot/windows-server/performance/windows-registry-advanced-users) (https://go.microsoft.com/fwlink/?LinkId=62729).

## In This Section

-   [General Guidelines for Improving Network Performance](../technical-guides/general-guidelines-for-improving-network-performance.md)

-   [Settings that can be Modified to Improve Network Performance](../technical-guides/settings-that-can-be-modified-to-improve-network-performance.md)

## See Also
 [Optimizing Performance](../technical-guides/optimizing-performance.md)