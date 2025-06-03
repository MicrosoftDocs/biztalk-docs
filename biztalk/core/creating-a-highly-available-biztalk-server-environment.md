---
description: "Learn more about: Creating a Highly Available BizTalk Server Environment"
title: "Creating a Highly Available BizTalk Server Environment"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Creating a Highly Available BizTalk Server Environment
This section describes how to provide high availability for the data and communications in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] when integrating disparate systems and applications. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] separates the data from the hosts that process the data, enabling you to resolve availability issues by scaling the databases and hosts independently.

## Demonstrating High Availability
 High availability for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] focuses on recovering functional components that might disrupt availability in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.

 To demonstrate high availability in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you have to apply failure and measure the product's effectiveness in recovery. A highly available [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment makes errors and failures transparent to external applications and systems, and makes sure that all services continue functioning correctly with minimal disruption.

## Designing for High Availability
 Designing a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment that provides high availability involves implementing redundancy for each functional component involved in an application integration or business process integration scenario. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] simplifies the implementation of these scenarios by conceptually separating the data from the hosts that process the data. So providing high availability for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] involves running multiple host instances and clustering the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, as follows:

- **Architecture for BizTalk Hosts** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lets you separate hosts and run multiple host instances to provide high availability for key functions such as receiving messages, processing orchestrations, and sending messages. These hosts do not require any additional clustering or load-balancing mechanism because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically distributes workload across multiple computers through host instances. However, hosts running the receive handler for the HTTP and SOAP adapters require a load-balancing mechanism such as Network Load Balancing (NLB) to provide high availability.

- **Architecture for BizTalk Server databases** High availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases typically consists of two or more database computers configured in an active/passive server cluster configuration. These computers share a common disk resource (such as a RAID5 SCSI disk array or storage area network) and use Windows Clustering to provide backup redundancy and fault tolerance.

> [!NOTE]
>  Highly-available environments are, by nature, multi-computer environments. When configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a multi-computer environment you must use domain user groups and accounts.

 Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is built on Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], and Microsoft SQL Server 2008, make sure that you deploy these products with high availability before configuring hosts for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The following links include information about providing high availability for these underlying products:

- **High Availability – Always On Technologies**, available at [https://go.microsoft.com/fwlink/?LinkId=130376](https://go.microsoft.com/fwlink/?LinkId=130376).

   This whitepaper describes high availability features that are available with SQL Server 2008.

- **High Availability Solutions Overview**, available at [https://go.microsoft.com/fwlink/?LinkId=130377](/sql/database-engine/sql-server-business-continuity-dr).

   Introduces several high-availability solutions for SQL Server 2008 that improve the availability of servers or databases.

- **Windows Deployment Services Step-by-Step Guide**, available at [https://go.microsoft.com/fwlink/?LinkId=130379](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771670(v=ws.10)).

   Contains step-by-step guidance for how to use the Windows Deployment Services role in Windows Server 2008.

- **Windows Server 2003 Deployment Kit: Planning Server Deployments**, available at [https://go.microsoft.com/fwlink/?LinkId=24433](/previous-versions/windows/it-pro/windows-server-2003/cc783586(v=ws.10)).

   This book provides information about planning server storage, and information about designing and deploying file servers, print servers, and terminal servers in medium and large organizations.

- **Increasing Availability for BizTalk Server**, available at [https://go.microsoft.com/fwlink/?LinkId=130457](https://go.microsoft.com/fwlink/?LinkId=130457).

   Section of the [BizTalk Server Operations Guide](https://go.microsoft.com/fwlink/?LinkId=130458) that describes ways you can increase the availability of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.

## In This Section

-   [Providing High Availability for BizTalk Hosts](../core/providing-high-availability-for-biztalk-hosts.md)

-   [Providing High Availability for BizTalk Server Databases](../core/providing-high-availability-for-biztalk-server-databases.md)

## See Also
 [Sample BizTalk Server High Availability Scenarios](../core/sample-biztalk-server-high-availability-scenarios.md)
 [Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)
