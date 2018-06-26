---
title: "Network Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, network configuration"
ms.assetid: fb6265b8-2e6d-4344-bb44-4f4fd995382d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Network Configuration
This section provides prescriptive guidance for configuring the network in your deployment. For more information, see [Preparing for Deployment](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md).  

 You define virtual local area networks (VLANs) in the switch and then connect the appropriate cables. By defining the VLANs, you are designating ports on the switch for each network segment or tier. You must create a VLAN for each of the following environments:  

- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive and send tier  

- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestration and database tier  

- Corporate network  

  After you have defined the VLANs, you can connect the network cables from the servers to the appropriate ports on the switch.  

  This section contains:  

- [Physical Diagram](../../adapters-and-accelerators/accelerator-swift/physical-diagram.md)  

- [Network Load Balancing](../../adapters-and-accelerators/accelerator-swift/network-load-balancing.md)
