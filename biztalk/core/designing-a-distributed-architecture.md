---
description: "Learn more about: Designing a Distributed Architecture"
title: "Designing a Distributed Architecture | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "clustering, SQL Servers"
  - "SQL Server, clustering"
ms.assetid: 8a8f1710-4d53-42bf-b5e5-2be3b43813b4
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Designing a Distributed Architecture
For complete information about the system architecture for BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).

 The architecture presented in the topic [Large Distributed Architecture](../core/large-distributed-architecture.md) addresses many of the potential security threats to which a BizTalk environment is vulnerable. While security should be high on your list of priorities when designing your architecture, there are additional considerations in a distributed environment, such as high-availability, scalability, and performance. This section provides additional options you can consider when designing your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architecture.

## Domains
 If your company performs mostly Internet-facing communications, you can remove the intranet services from the corporate domain. Conversely, if you use BizTalk Server to connect to other applications or business partners that connect through the intranet, you can remove the perimeter network. If your company does both Internet and intranet-facing communications with a small number of partners, you may consider combining the intranet services and the perimeter network.

 If you want to minimize the latency in the communication between the processing servers and the SQL Servers in the data domain, and security issues such as network sniffing, tampering of packets, and host spoofing in the internal network are not a concern, you can remove the firewall between the processing and data domain, and merge these domains. It is recommended you then use Internet Protocol security (IPSec) or Secure Sockets Layer (SSL) to protect the data as it goes from one server to another.

## SQL Server clustering
 Although not described in detail in this section, we strongly recommend clustering your databases for failover protection. For more information about SQL Server 2008 failover clustering, see the Microsoft MSDN Web site at [https://go.microsoft.com/fwlink/?LinkId=131016](/previous-versions/sql/sql-server-2008-r2/ms178094(v=sql.105)).

## MessageBox database
 Depending on the message throughput requirements for your company, you may need to add (or remove) MessageBox databases. For more information about multiple messagebox, see [Scaled-Out Databases](../core/scaled-out-databases.md).

## See Also
 [Designing a Secure Architecture](../core/designing-a-secure-architecture.md)
 [Planning for High Availability](../core/planning-for-high-availability3.md)
 [Planning for Sustained Performance](../core/planning-for-sustained-performance.md)
 [Designing the System Architectures for BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md)
 [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md)