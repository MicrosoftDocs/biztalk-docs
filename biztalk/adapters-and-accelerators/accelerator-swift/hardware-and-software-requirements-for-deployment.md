---
title: "Hardware and Software Requirements for Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, hardware requirements"
  - "deploying, software requirements"
ms.assetid: 1dd9c4bb-b724-4195-8496-eff95cd1548a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Hardware and Software Requirements for Deployment
The following table lists the hardware and software recommendations and requirements for each server in the prescribed deployment architecture. For details about configuring required software, see [Deploying Your Servers](../../adapters-and-accelerators/accelerator-swift/deploying-your-servers.md).  

 For all server types, choose the hard-disk space, the processor clock speed, and the amount of random access memory (RAM) based upon the current and projected technical requirements (as described in [Step 1: Installing the Base Platform](../../adapters-and-accelerators/accelerator-swift/step-1-installing-the-base-platform.md)).  


|                    Server                    |                                                                                                                                           Hardware recommendations                                                                                                                                            |                                                                                                                                                   Software requirements                                                                                                                                                    |
|----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|             Domain controller(s)             |                                                                                                                                             -   1 network adapter                                                                                                                                             |                                       -   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Windows Server 2012 R2 or 2012<br />-   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsAD](../../includes/btsad-md.md)] Server<br />-   Domain Name Server (DNS)                                       |
|           Microsoft SQL Server(s)            | -   2 network adapters<br />-   Optional: For the Storage Area Network (SAN) disks, choose the hard-disk space required for the average throughput, peak throughput, and peak throughput time plus average message size. The SAN should be partitioned into three drives: data, transaction logs, and quorum. |                                                                        -   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Windows Server 2012 R2 or 2012<br />-   [!INCLUDE[SQLServer2008or2005](../../includes/sqlserver2008or2005-md.md)]                                                                         |
|       BizTalk Server(s) for messaging        |                                                                                                                                            -   2 network adapters                                                                                                                                             |                                                  -   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Windows Server 2012 R2 or 2012<br />-   BizTalk Server<br />-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]                                                   |
| BizTalk HTTP front-end server(s) (MRSR site) |                                                                                                                                            -   2 network adapters                                                                                                                                             | -   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Windows Server 2012 R2 or 2012<br />-   Internet Information Services (IIS)<br />-   Message Queuing service with routing enabled<br />-   BizTalk Server<br />-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] |
|     BizTalk Server(s) for orchestrations     |                                                                                                                                             -   1 network adapter                                                                                                                                             |                                                  -   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Windows Server 2012 R2 or 2012<br />-   BizTalk Server<br />-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]                                                   |

