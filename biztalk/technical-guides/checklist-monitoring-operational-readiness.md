---
title: "Checklist: Monitoring Operational Readiness | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef77ccc2-1d39-4e78-8fea-5c17d05c8174
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Monitoring Operational Readiness
This topic lists the steps that you should follow when monitoring a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.  


|                                                                                                                                                                      Steps                                                                                                                                                                       |                                                                                                  Reference                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                           Select and implement a monitoring strategy for your BizTalk applications and infrastructure.                                                                                                                           |                                                [Monitoring the BizTalk Server Environment](../technical-guides/monitoring-the-biztalk-server-environment.md)                                                 |
|                                                                                                                                                            Monitor disk space usage.                                                                                                                                                             |                                                              [Monitoring Disk Space Usage](../technical-guides/monitoring-disk-space-usage.md)                                                               |
| Monitor SQL Server:<br /><br /> -   Verify that computers running SQL Server housing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are being monitored.<br />-   Verify that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] jobs are being monitored. |            -   [Monitoring SQL Servers](../technical-guides/monitoring-sql-servers.md)<br />-   [Monitoring BizTalk Server Databases](../technical-guides/monitoring-biztalk-server-databases.md)            |
|          Monitor BizTalk applications:<br /><br /> -   Modify existing rules and/or copy rules to a custom management pack to monitor a custom BizTalk application.<br />-   Create actions for each defined rule.<br />-   Create iterative processes to automate manual tasks.<br />-   Use threshold rules to automate manual tasks.          | -   [Monitoring Applications and Host Instances](../technical-guides/monitoring-applications-and-host-instances.md)<br />-   [Monitoring BizTalk Server2](../technical-guides/monitoring-biztalk-server2.md) |

## In This Section  

-   [Monitoring Disk Space Usage](../technical-guides/monitoring-disk-space-usage.md)