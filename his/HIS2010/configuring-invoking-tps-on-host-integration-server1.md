---
title: "Configuring Invoking TPs on Host Integration Server1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ce0fa9dd-1f9d-4c8e-8b64-f2ec75696619
caps.latest.revision: 3
---
# Configuring Invoking TPs on Host Integration Server
For a server running [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] to support the beginning of the invoking process (that is, to accept the [TP_STARTED](../HIS2010/tp-started1.md) and [ALLOCATE](../HIS2010/allocate1.md) or [MC_ALLOCATE](../HIS2010/mc-allocate1.md) verbs issued by an invoking TP), the following parameters must be configured correctly:  
  
-   If the invoking TP specifies in **TP_STARTED** the LU alias that it uses, that LU alias must match a local APPC LU alias on the supporting server running [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]. If the invoking TP leaves the LU alias blank in **TP_STARTED**, one of two methods for designating a default LU must be carried out on the supporting server running [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]:  
  
    -   Assign a default local APPC LU to the user or group that starts the invoking TP (that is, the user or group logged on at the system from which **TP_STARTED** is issued).  
  
    -   Designate one or more LUs as members of the default outgoing local APPC LU pool. The Host Integration Server first attempts to determine the default local APPC LU of the user who started the TP, and then attempts to assign an available LU from the default outgoing local APPC LU pool; if these attempts fail, the Host Integration Server rejects the request.  
  
-   In most situations, the supporting Host Integration Server must contain an appropriate connection to another system (host or peer). Sometimes, for testing purposes, the server running [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] contains two local LUs paired together (for invoking and invokable TPs that are in the same domain); in this situation, a connection to a host or peer is not necessary.  
  
-   If the invoking TP specifies in [ALLOCATE](../HIS2010/allocate1.md) or [MC_ALLOCATE](../HIS2010/mc-allocate1.md) the partner LU alias, that LU alias must match an LU alias that is paired with the local LU alias specified in [TP_STARTED](../HIS2010/tp-started1.md). If the partner LU alias is left unspecified in **ALLOCATE** or **MC_ALLOCATE**, a default remote APPC LU must be assigned to the user who started the invoking TP. The default remote APPC LU is configuring using SNA Manager on [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]. If the default remote APPC LU is used, it must be paired with the local LU that will be used. Otherwise, **ALLOCATE** or **MC_ALLOCATE** fails.  
  
 The preceding parameters support the beginning of the invoking process. For the invoking process to successfully complete, additional parameters must be configured as described in [Configuring Invokable TPs on Host Integration Server](../HIS2010/configuring-invokable-tps-on-host-integration-server2.md).