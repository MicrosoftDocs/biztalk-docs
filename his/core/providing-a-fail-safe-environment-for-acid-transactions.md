---
title: "Providing a Fail-Safe Environment for ACID Transactions1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4cbc41a-bdf8-406d-920c-423b9c1ab782
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Providing a Fail-Safe Environment for ACID Transactions
ACID (atomic, consistent, isolated, and durable) transaction processing using two-phase commit (2PC) generally requires a fail-safe environment, which is an environment that ensures continuation in spite of hardware failures. This is often called 2PC failover or hot backup.  
  
 [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] includes enhancements to the **SNA LU 6.2 Resync TP** commonly called the Resync service along with enhancements to the configuration and APPC DLL to make 2PC failover work through two or more redundantly configured Host Integration Server SNA servers (computers). In the event of a failure of one of the servers (computers), a separate Host Integration Server computer running either TI or the DB2 Provider can continue to initiate transactions through an alternate server (computer).  
  
 To configure 2PC failover to work with Host Integration Server, complete these tasks:  
  
-   Configure two [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] servers to support the same SyncPoint-enabled local APPC LU alias but with different LU names. Have these local APPC LUs point to the same computer name where Microsoft Distributed Transaction Coordinator (DTC) service and the Resync service are running (that is, a separate Host Integration Server computer that supports TI or an application that uses the DB2 Provider). Also, have both servers support the same remote APPC LU alias and name.  
  
-   In the applicable TI remote environment (RE), configure the local and remote LU aliases, and choose transactional support. If the application is using the DB2 Provider, configure the Universal Data Link with the local and remote APPC LU aliases, and set the **Units of Work** property to DUW.  
  
 When the Resync service starts, it searches all SyncPoint-enabled local APPC LUs that specify the computername where the Resync service is running. Resync then initiates an Exchange Log Names request over every found local APPC LU with all SyncPoint-enabled remote APPC LUs.  
  
 When a TI Automation server (application) or the DB2 Provider invokes a transaction program (TP) on the mainframe and initiates a conversation, the APPC DLL locates any available [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] server (computer) that supports the LU/LU pair.  
  
 In this way, a TI Automation server (application) or the DB2 Provider gains fault tolerance by getting a conversation through any [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] server (computer) that supports the LU/LU pair. The Resync service then coordinates the DTC transaction log reconciliation when a Host Integration Server SNA server (computer) comes back online, if a server (computer) failure occurs during a transaction. Note that this configuration does not provide fault tolerance for the [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] server (computer) that is running only TI or the DB2 Provider, not the SNA service.  
  
> [!NOTE]
>  Clustering the servers (computers) that are running the SNA service is not recommended. Instead of using Windows Clustering, use the configuration recommendations described in this topic.  
  
> [!NOTE]
>  2PC works only when you are using the SNA (APPC/LU 6.2) protocol to communicate with the host system. Neither TI nor the DB2 Provider support 2PC over the TCP/IP transport, so there is no 2PC failover solution for TCP/IP-based systems.  
  
## See Also  
 [Windows-Initiated Processing](../core/windows-initiated-processing.md)