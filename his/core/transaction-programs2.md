---
title: "Transaction Programs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c09f0f8b-19b0-4d10-8e7a-06dea8dda7c1
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Transaction Programs
The part of an application that initiates or responds to APPC communications is called a transaction program (TP). TPs use APPC to exchange data with other TPs on a peer-to-peer basis.  
  
 Similar to a conversation when people talk with each other, the communication between two transaction programs is called a conversation. An application running on your computer can have many conversations active at one time, either with one other transaction program or with different transaction programs.  
  
 There are two types of TPs: TPs that can invoke (initiate a conversation with) other TPs, and TPs that can be invoked. A TP that can invoke another TP is called an invoking TP, and a TP that can be invoked is called an invokable TP.  
  
 If your [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] installation contains multiple systems (client computers or [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computers), you can place invokable TPs on more than one system. When an invoking request is received in such an installation, there will (potentially) be a choice of systems on which to run the invokable TP. You can maintain specific control over this choice, or you can allow the choice to be made randomly by Host Integration Server (to distribute the load).  
  
 You can maintain specific control over this choice of system by setting up invokable TPs with unique names, or by setting up each invokable TP to run only with a specific, unique LU alias. With this arrangement, the information provided by the invoking TP (in the ALLOCATE verb) can specify the particular system on which the TP should run.  
  
 You can avoid controlling this choice of system, and allow the choice to be made randomly by Host Integration Server, by setting the **DloadMatchLocalFirst** registry entry to **NO**, as described in the *Host Integration Server Administrators Reference*. Then use invokable TPs that leave the local LU alias unspecified. When an incoming request is received, it is routed randomly, rather than preferentially, to the local Host Integration Server computer. In addition, no matter what LU alias is requested for the invokable TP, there cannot be a mismatch. Host Integration Server will start the TP, choosing randomly among the available systems.  
  
 Following are three of the possible ways that TPs can be arranged to run.  
  
## In This Section  
 [TP Name Unique for Each TP (Transaction Programs)](../core/tp-name-unique-for-each-tp-transaction-programs-1.md)  
  
 [TP Name Not Unique; Local LU Alias Unique](../core/tp-name-not-unique;-local-lu-alias-unique2.md)  
  
 [TP Name Not Unique; Local LU Alias Unspecified](../core/tp-name-not-unique;-local-lu-alias-unspecified2.md)  
  
 [Invoking Transaction Programs](../core/invoking-transaction-programs1.md)  
  
 [Invoking TPs and Host Integration Server Configuration](../core/invoking-tps-and-host-integration-server-configuration1.md)  
  
 [Invokable Transaction Programs](../core/invokable-transaction-programs2.md)  
  
 [Invokable TPs and the Host Integration Server Configuration](../core/invokable-tps-and-the-host-integration-server-configuration1.md)  
  
## See Also  
 [Understanding Connectivity](../core/understanding-connectivity1.md)