---
title: "Planning the BizTalk Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30d56a04-966a-46b1-861d-f5be4e58b7d2
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Plan for your BizTalk Solution
One of the primary design goals of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is to provide maximum flexibility for accommodating as many processing scenarios as possible. Because of this great flexibility, one of the primary challenges facing developers of a BizTalk solution is to determine how to make best use of the features available in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to best meet their business needs. Planning the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be broken down into distinct phases which are summarized below.  
  
## Scoping the Solution  
  
### Performance Considerations  
 Consider the following when scoping your BizTalk solution:  
  
- Which adapters and/or accelerators are required?  
  
- What are the requirements for implementing orchestrations in the solution?  
  
- Document throughput requirements: What are the maximum sustainable throughput requirements for the solution?  
  
- Latency requirements: How responsive does the solution need to be for solicit-response and request-response scenarios?  
  
- How well does the solution recover from periods of peak document load?  
  
- What are the high availability requirements of the solution?  
  
- What are the document tracking requirements of the solution?  
  
- What are the performance characteristics of any dependent applications such as a remote Web service or other system? If dependent applications do not keep up with the required load then the overall system performance will be degraded accordingly.  
  
- Would the BizTalk application be consuming databases not related to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]? For example, if the BizTalk application is consuming tables in a SQL Server database using the SQL adapter, are the tables efficiently configured?  
  
### Hardware Considerations  
 When scoping the solution, create a high-level hardware diagram that includes the following:  
  
-   Computer architecture (such as x86, x64, and IA64)  
  
-   CPU requirements (such as type, speed, number, cores, and use of hyperthreading)  
  
-   RAM requirements for each computer  
  
-   Local disk storage (type, size, speed)  
  
-   SAN (storage requirements: number of LUNS; SAN card type)  
  
-   Network cards (number in each computer, 100 megabits (Mbps) versus 1 Gigabit (1 Gbps).)  
  
-   How will firewalls be deployed in the solution?  
  
-   Will Network Load Balancing hardware be used?  
  
-   Are specific computers to be clustered?  
  
-   Would you be using a virtual environment involving Microsoft Hyper-V Server or any other virtualization products?  
  
## Planning the Solution  
  
### Solution Milestones Timeline  
 Create a schedule with milestones for completing specific aspects of your BizTalk solution. Setting specific milestones will increase the likelihood that the solution will be completed in a timely manner.  
  
### Non-Microsoft Software Considerations  
 Consider the following when non-Microsoft software will be used with the solution:  
  
-   Determine how the software or hardware required be obtained.  
  
-   Plan for capacity and sizing to ensure that non-Microsoft software does not become a bottleneck in your solution.  
  
-   Determine a plan of action for installing required non-Microsoft software.  
  
-   Create a plan of action for configuring and optimizing required non-Microsoft software.  
  
## Preparing for the Solution  
 Include the following elements in your preparation phase:  
  
### Detailed Design of the Solution Platform  
 A detailed solution design facilitates communications and avoids assumptions, which will improve the agility and effectiveness of all activities. You should fully document the following elements:  
  
- BizTalk Server databases and how they will be distributed across computers.  
  
- BizTalk Host design and descriptions of each host and their instances.  
  
- Description of each orchestration.  
  
- Description of each pipeline.  
  
- Description of custom components such as .NET assemblies and COM+ components.  
  
  **Message Flow Diagrams**  
  
  Create detailed message flow diagrams to help avoid any confusion or false assumptions regarding what is supposed to be happening to messages during processing. The following details should be considered when creating the message flow diagrams:  
  
- Describe the lifecycle of each type of message from the time it arrives at a receive location until all resulting messages are sent and all related processing is completed.  
  
- Describe how processing changes for error conditions.  
  
- Include details about correlation, delivery notifications, and acknowledgements.  
  
- Include performance requirement information regarding latency and throughput.  
  
  **Non-Microsoft Software Details**  
  
  All non-Microsoft software that is used should be fully documented as part of the detailed solution design.  
  
  **Detailed Hardware Stack**  
  
  Building on the previously created high level hardware diagram, the following hardware information should be fully documented:  
  
- Processors  
  
  -   Type  
  
  -   Speed  
  
  -   Number of cores  
  
  -   Hyperthreading  
  
- Memory  
  
  -   Amount  
  
  -   Speed  
  
  -   Parity  
  
- Network  
  
  -   Number of network interface cards (NICs)  
  
  -   Speed of network  
  
- SAN  
  
  -   Number of SAN cards in each computer  
  
  -   Number of logical unit numbers (LUNs) for each computer and purpose for each LUN  
  
  -   Speed of storage area network (SAN) Cards  
  
  -   SAN card configuration details  
  
  -   SAN disk allocation, formatting, and partitioning  
  
- Disk  
  
  -   Local disk details for each computer  
  
  -   Formatting used for local disks  
  
  -   Partitioning details for local disks  
  
- Cache  
  
  -   L2 Cache amount  
  
  -   L3 Cache amount  
  
  **Detailed Software Stack**  
  
  The following software information should be documented:  
  
- Specific operating system versions, editions, and architecture  
  
- Specific operating system features  
  
- Specific software installed on each computer  
  
- Specific drivers  
  
- Service Packs and other updates  
  
- Configuration values for all software and operating system features used if they vary from default values  
  
## Building Out the Environment for the Solution  
 Detailed instructions for installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the software requirements are in the [BizTalk Server Installation Guides](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).
  
## See Also  
 [Planning the BizTalk Server Tier](../technical-guides/planning-the-biztalk-server-tier.md)
