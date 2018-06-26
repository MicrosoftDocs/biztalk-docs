---
title: "Configuring Invoking TPs on Host Integration Server2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3cf83d53-2937-408c-8ff6-278ee4de1b43
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring Invoking TPs on Host Integration Server
For a server running Host Integration Server to support the beginning of the invoking process (that is, to accept the [TP_STARTED](./tp-started2.md) and [ALLOCATE](./allocate2.md) or [MC_ALLOCATE](./mc-allocate2.md) verbs issued by an invoking TP), the following parameters must be configured correctly:  
  
- If the invoking TP specifies in **TP_STARTED** the LU alias that it uses, that LU alias must match a local APPC LU alias on the supporting server running Host Integration Server. If the invoking TP leaves the LU alias blank in **TP_STARTED**, one of two methods for designating a default LU must be carried out on the supporting server running Host Integration Server:  
  
  -   Assign a default local APPC LU to the user or group that starts the invoking TP (that is, the user or group logged on at the system from which **TP_STARTED** is issued).  
  
  -   Designate one or more LUs as members of the default outgoing local APPC LU pool. The Host Integration Server first attempts to determine the default local APPC LU of the user who started the TP, and then attempts to assign an available LU from the default outgoing local APPC LU pool; if these attempts fail, the Host Integration Server rejects the request.  
  
- In most situations, the supporting Host Integration Server must contain an appropriate connection to another system (host or peer). Sometimes, for testing purposes, the server running Host Integration Server contains two local LUs paired together (for invoking and invokable TPs that are in the same domain); in this situation, a connection to a host or peer is not necessary.  
  
- If the invoking TP specifies in [ALLOCATE](./allocate2.md) or [MC_ALLOCATE](./mc-allocate2.md) the partner LU alias, that LU alias must match an LU alias that is paired with the local LU alias specified in [TP_STARTED](./tp-started2.md). If the partner LU alias is left unspecified in **ALLOCATE** or **MC_ALLOCATE**, a default remote APPC LU must be assigned to the user who started the invoking TP. The default remote APPC LU is configuring using SNA Manager on Host Integration Server. If the default remote APPC LU is used, it must be paired with the local LU that will be used. Otherwise, **ALLOCATE** or **MC_ALLOCATE** fails.  
  
  The preceding parameters support the beginning of the invoking process. For the invoking process to successfully complete, additional parameters must be configured as described in [Configuring Invokable TPs on Host Integration Server](../core/configuring-invokable-tps-on-host-integration-server1.md).