---
title: "Invoking TPs and Host Integration Server Configuration1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f2236d4-39bf-4ed7-bd5f-ca241ac78e9f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Invoking TPs and Host Integration Server Configuration
For Host Integration Server to support the beginning of the invoking process (to accept the TP_STARTED and ALLOCATE verbs issued by an invoking TP), the following parameters must be configured correctly:  
  
- If the invoking TP specifies the LU alias that it uses (in TP_STARTED), that LU alias must match a local APPC LU alias on the supporting Host Integration Server computer.  
  
- If the invoking TP leaves the LU alias blank in TP_STARTED, one of two methods for designating a default LU must be used on the supporting Host Integration Server:  
  
  - Assign a default local APPC LU to the user or group that starts the invoking TP (the user or group logged on at the system from which TP_STARTED is issued).  
  
     – or –  
  
  - Designate one or more LUs as members of the default outgoing local APPC LU pool.  
  
    If the invoking TP leaves the LU alias blank in TP_STARTED, Host Integration Server first attempts to determine the default local APPC LU of the associated user or group, and then attempts to assign an available LU from the default outgoing local APPC LU pool. If these attempts fail, Host Integration Server rejects the TP_STARTED request.  
  
- In most situations, the supporting Host Integration Server must contain an appropriate connection to another system (host or peer). Sometimes, for testing purposes, Host Integration Server contains two local LUs paired together (for invoking and invokable TPs that are in the same domain). In this situation, a connection to a host or peer is not necessary.  
  
- If the invoking TP specifies the partner LU alias (in ALLOCATE), that LU alias must match a remote LU alias. In addition, that remote LU alias must be paired with the local LU alias specified in TP_STARTED. If the LU alias is left blank in ALLOCATE, a default remote APPC LU must be assigned to the user who started the invoking TP. If the default remote APPC LU is used, it must be paired with the local LU that will be used. Otherwise, the ALLOCATE verb fails.  
  
  The preceding parameters support the beginning of the invoking process. For the invoking process to successfully complete, additional parameters must be configured on another Host Integration Server computer, as described in the next section.  
  
## See Also  
 [Transaction Programs](../core/transaction-programs2.md)   
 [TP Name Unique for Each TP (Transaction Programs)](../core/tp-name-unique-for-each-tp-transaction-programs-1.md)   
 [TP Name Not Unique; Local LU Alias Unique](../core/tp-name-not-unique;-local-lu-alias-unique2.md)   
 [TP Name Not Unique; Local LU Alias Unspecified](../core/tp-name-not-unique;-local-lu-alias-unspecified2.md)   
 [Invoking Transaction Programs](../core/invoking-transaction-programs1.md)   
 [Invokable Transaction Programs](../core/invokable-transaction-programs2.md)   
 [Invokable TPs and the Host Integration Server Configuration](../core/invokable-tps-and-the-host-integration-server-configuration1.md)