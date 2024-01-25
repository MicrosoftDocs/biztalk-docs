---
description: "Learn more about: Planning for Performance"
title: "Planning for Performance"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Planning for Performance
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is an application platform. It is not just a server product or just a developer product. It is an application platform that is used to build business process management systems, to integrate enterprise applications, to automate workflows, and to enable service oriented architectures.

 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is dependent on many other software components. The BizTalk application platform typically includes several of the following software components: the Windows Server operating system, SQL Server, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], IIS (optional), external systems that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is interacting with, as well as non-Microsoft adapters and components.

 Because of the inherently complex nature of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, there are many considerations to be made when planning for performance. There are several default settings that are applicable to all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environments and there are additional considerations and methodologies for optimizing specific [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architectures.

 This topic provides an overview of the default settings that you should apply when optimizing performance for all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environments. It also provides recommendations for testing and optimizing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environments that are designed for specific scenarios.

## Settings That You Should Apply to All BizTalk Server Environments
 The [Operational Readiness Checklists](../technical-guides/operational-readiness-checklists.md) section of this guide contains a list of items that you should review before employing any BizTalk solution. This checklist contains action items that can have a significant impact on the performance of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment regardless of the specific nature of the BizTalk solution that is employed.

## Considerations for Testing and Optimizing a BizTalk Solution
 Different BizTalk solutions may have drastically different performance criteria. For example, a BizTalk solution that is built around running orchestrations will have a different performance profile than a BizTalk solution that is focused on receiving, converting, and mapping flat file documents. An orchestration-focused solution may be CPU intensive or may call custom components that benefit from optimization, while a flat file conversion and mapping-focused solution may be more memory-intensive.

 The adapters and pipelines used to receive and send documents in and out of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can also have a profound impact on the performance of the BizTalk solution. The level of document tracking required by the solution will also greatly impact performance. Because of the many divergent performance profiles that are possible in different BizTalk solutions, it is absolutely critical that you test the BizTalk solution to measure maximum sustainable performance and maximum sustainable tracking performance.

 After determining the maximum sustainable performance and maximum sustainable tracking performance of the BizTalk solution, there are specific steps that you can employ to remove bottlenecks in the BizTalk solution. For more information, see the [BizTalk Server 2009 Performance Guide](https://go.microsoft.com/fwlink/?LinkID=150492) (https://go.microsoft.com/fwlink/?LinkID=150492).

## See Also
 [Planning the BizTalk Server Tier](../technical-guides/planning-the-biztalk-server-tier.md)
