---
title: "Support for Transactions and Two-Phase Commit2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ad9480e-f1a6-4ae6-8da0-d4904d1fa87c
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Support for Transactions and Two-Phase Commit
In COM termwinology, a transaction is always a unit of work that is atomic, consistent, isolated, and durable (ACID). In mainframe terminology, a transaction may or may not be an ACID transaction; in mainframe terminology, a transaction is a set of operations or commands in a transaction program (TP). This difference in terminology can be confusing. The word transaction as it is used in TI Manager and TI Designer always refers to an ACID transaction.  
  
 Two-phase commit (2PC) is a protocol that allows a set of application (or cross-application) operations or commands to be either all rolled back or all committed as a single transactional unit.  
  
> [!NOTE]
>  If you invoke a TI Automation server over the TCP/IP protocol, there is no support for two-phase commit transactions. Two-phase commit works only over the SNA APPC/LU 6.2 protocol.  
  
 A TI component has four possible transactional properties:  
  
- Requires transaction  
  
- Requires new transaction  
  
- Supports transactions  
  
- Does not support transactions  
  
  The first two choices require the mainframe TP to be transactional (that is, meet the ACID properties) and to support Sync Level 2. This is transparent to the mainframe TP if it is a CICS Link or IMS version 6.0 or later program. The third choice requires the mainframe TP to support Sync Level 2 requests and handle the transaction semantics appropriately. The fourth choice is required for IMS TPs prior to IMS version 6.0 and for any CICS TPs that support only Sync Level 0 or Sync Level 1.  
  
  If a TI component is invoked within the scope of a COM+ transaction, TI will establish a Sync Level 2 conversation with CICS (otherwise, Sync Level 0 is used). This is transparent to the client of the TI component. If the mainframe TP is a CICS Link program, the transactional nature of the conversation is transparent to the TP as well, since IBM's mirror transaction in CICS (CSMI) handles the Sync Level 2 protocol, and the TP to which it is linked is unaware whether Sync Level 0 or Sync Level 2 is being used.  
  
  TI complies with the COM+ programming model by calling SetComplete or SetAbort when it completes the operation of each method call from the client. If no errors were detected, TI calls SetComplete; otherwise it calls SetAbort. TI also calls SetAbort if the mainframe TP indicates that the transaction should not commit by setting the DisableCommit flag in the meta data error block returned. TI Automation client applications can also choose to call SetAbort if they determine that there are application-level problems that should prohibit the transaction from committing.  
  
  When the client's method call returns, the TP on the mainframe has performed some unit of work, but any changes to protected resources in CICS are not yet committed. TI uses new DTC interfaces to enlist the Sync Level 2 conversation on the DTC transaction. When DTC is ready to commit or abort the transaction, it communicates with TI to drive the appropriate two-phase commit flows on the LU 6.2 conversation. Again, all of the 2PC work is performed transparently by TI on the client's behalf.  
  
  Although the TI object can be deactivated when the method completes, the conversation must be maintained until the transaction commits or aborts. Users can adversely affect performance and tie up system resources if their application code makes one or more transactional method calls but does not commit the transaction for a long period of time. Conversations can be quickly consumed by poorly structured user code.  
  
  When a conversation is waiting to commit, it will be divorced from the object with which it was associated. TI manages a pool of these "waiting" conversations and performs the required sync-level operations when the appropriate notifications are received from DTC. When possible, TI reuses these conversations to minimize overhead.  
  
  TI also provides a resynchronization service (SNA LU 6.2 Resync TP). This Windows service is configured to be the auto-started invokable service for the SNA-defined Resync TP (0x06f2). The Resync service implements the "Exchange Log Names" and "Compare States" functions of an SNA transaction manager. It allows both DTC (Distributed Transaction Coordinator) and CICS to initiate the recovery process as required during system startup or following a system or communication failure.  
  
  For information about IBM's SNA SyncPoint or 2PC flows, *SNA SyncPoint Services Architecture Reference (IBM SC31-8134-00)*. All TI 2PC flows are implemented in conformance with this architecture.  
  
> [!NOTE]
>  For information on how to use CICS Link TPs that use explicit SYNCPOINT commands, see **TPs with Explicit SYNCPOINT Commands**.  
  
 In summary, to use two-phase commit, you must meet all of the following requirements:  
  
- The local and remote LUs must each have SyncPoint support enabled in the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] node.  
  
- The local and remote LUs should each point to the computer that is running Resync services.  
  
- The remote environment (RE) must have Sync Level 2 support enabled. To check this, right-click the RE in TI Manager, click Properties, and then click the LU 6.2 tab.  
  
- The TI component must have Transaction Support set to Supported, Required, or Requires New. To check this setting, right-click the TI component in TI Manager, click Properties, and then click the Transactions tab.  
  
- The remote host computer must be configured for Sync Level 2 support.  
  
## See Also  
 [WIP Programming Model](../core/wip-programming-model2.md)