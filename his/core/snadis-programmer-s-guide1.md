---
title: "SNADIS Programmer&#39;s Guide1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc707f56-483e-4de2-99e4-e90e0213738f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SNADIS Programmer&#39;s Guide
This section enables original equipment manufacturers (OEMs) and adapter vendors who are developing their own SNALink software to work with Host Integration Server SNA Services.  

 SNALink software must be written as a Microsoft Windows device driver. For information about writing Windows device drivers, see the Windows Device Driver Kit (DDK).  

 This section provides the following information:  

- Internal concepts of Host Integration Server that are required to integrate new communications adapters into the server environment.  

- Definitions of the interfaces used by Host Integration Server to communicate with SNALinks.  

- Information about using the configuration and diagnostics features included in Host Integration Server.  

- Instructions for compiling and linking the SNALink support software.  

  The network operating systems currently supported by Host Integration Server include Microsoft LAN Manager (as implemented in Microsoft Windows) and TCP/IP. Future versions of Host Integration Server may support other network operating systems. Because of this, it is recommended that you develop link support that is independent of the network operating system.  

  For API references and other technical materials for programming SNALink applications, see the [SNADIS Drivers Programmer's Reference](./snadis-drivers-programmer-s-reference2.md) section of the SDK.  

  This section contains:  

- [SNALink Concepts in Host Integration Server](../core/snalink-concepts-in-host-integration-server1.md)  

- [SNALink Interface](../core/snalink-interface1.md)  

- [SNALink Configuration Information](../core/snalink-configuration-information1.md)  

- [Data Link Control Interface](../core/data-link-control-interface1.md)  

- [Setup Information (SNADIS)](../core/setup-information-snadis-1.md)  

- [Compiling and Linking a SNALink](../core/compiling-and-linking-a-snalink2.md)  

- [Synchronous Dumb Card Interface](../core/synchronous-dumb-card-interface1.md)  

- [SNA Modem Status Interface](../core/sna-modem-status-interface1.md)  

- [SNA Performance Monitor Interface](../core/sna-performance-monitor-interface1.md)
