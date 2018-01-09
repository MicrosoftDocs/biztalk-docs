---
title: "Supporting Two-Phase Commit in a Remote Environment1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a37afb7a-0f96-4095-ac49-3dbf01323491
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Supporting Two-Phase Commit in a Remote Environment
Only the SNA protocols support two-phase commit (2PC). The TCP/IP protocol does not support 2PC. For an SNA remote environment (RE) to support 2PC, it must be set to support ACID (atomic, consistent, isolated, durable) transactions. To accomplish this, you must set the RE to support the Sync Level 2 protocol.  
  
 Transaction Integrator (TI) supports Sync Level 2 for CICS Using LU 6.2, for CICS LINK Using LU 6.2, and for IMS Using LU 6.2 REs. Sync level 2 is the default for all CICS REs but not for IMS REs where IMS version 6.0 and IBM's Resource Recovery Services (RRS) are required for Sync Level 2 support.  
  
 To activate Sync Level 2 support, follow the procedure in [How to Define a Transactional SNA CICS or SNA IMS Remote Environment](../core/how-to-define-a-transactional-sna-cics-or-sna-ims-remote-environment2.md).  
  
> [!NOTE]
>  The [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] LU 6.2 Resync TP Service only compares logs with CICS and IMS regions when the RE has been set to support Sync Level 2.  
  
## See Also  
 [Creating and Managing Remote Environments with TI Manager](../core/creating-and-managing-remote-environments-with-ti-manager1.md)   
 [Creating and Managing TI Components](../core/creating-and-managing-ti-components2.md)   
 [Getting Started with TI](../core/getting-started-with-ti1.md)