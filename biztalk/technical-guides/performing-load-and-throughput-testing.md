---
description: "Learn more about: Performing Load and Throughput Testing"
title: "Performing Load and Throughput Testing"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Performing Load and Throughput Testing
You should make available an environment that matches your production environment for performance and stress testing. This environment should have all standard services installed and running, such as monitoring agents and antivirus software.

## How Adding Applications Affects Load
 You should also test new BizTalk applications alongside the other BizTalk applications that are going to run on the same hardware in production. This is because the new BizTalk applications put additional load on the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server. This is especially important in light of the host throttling algorithms that are used in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The throttling algorithm monitors total available resources and hence the additional load incurred by a new BizTalk application may induce a throttling condition which affects all running BizTalk applications. For more information, see [How BizTalk Server Implements Host Throttling](../core/how-biztalk-server-implements-host-throttling.md) (<https://go.microsoft.com/fwlink/?LinkId=154389>).

## Testing Load and Determining Recovery Time
 You should test all BizTalk applications for performance and stress before you put them into production. You should perform your testing against expected loads and against peak loads. You should determine the maximum sustainable throughput (MST) for the BizTalk application. In addition, you should determine how long it takes the system to recover from peak loads. If the system does not fully recover from a peak load before the next peak load occurs, then the system will get progressively farther behind and will not be able to fully recover. For more information, see:

-   [Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md) (https://go.microsoft.com/fwlink/?LinkId=154388)

-   [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md) (https://go.microsoft.com/fwlink/?LinkID=153815)

## See Also
 [Checklist: Testing Operational Readiness](../technical-guides/checklist-testing-operational-readiness.md)
