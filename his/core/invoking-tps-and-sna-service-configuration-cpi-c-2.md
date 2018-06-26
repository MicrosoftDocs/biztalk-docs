---
title: "Invoking TPs and SNA Service Configuration (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3efe0eda-832c-4c23-8a90-2dedacdd70ff
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Invoking TPs and SNA Service Configuration (CPI-C)
For an SNA service to support the beginning of the invoking process, the following parameters must be configured correctly:  
  
- If the invoking transaction program (TP) specifies the logical unit (LU) alias that it uses (in a registry or environment variable), that LU alias must match a local Advanced Program-to-Program Communications (APPC) LU alias on the supporting SNA service. If the invoking TP does not specify a local LU alias, one of two methods for designating a default LU must be carried out on the supporting SNA service:  
  
  -   Assign a default local APPC LU to the user or group that starts the invoking TP (that is, the user or group logged on at the system from which [Initialize_Conversation](./initialize-conversation-cpi-c-1.md) is issued).  
  
       —or—  
  
  -   Designate one or more LUs as members of the default outgoing local APPC LU pool. Host Integration Server or SNA service first attempts to determine the default local APPC LU of the user who started the TP, then attempts to assign an available LU from the default outgoing local APPC LU pool. If these attempts fail, SNA service rejects the request.  
  
- In most situations, the supporting SNA service must contain an appropriate connection to another system (host or peer). Sometimes, for testing purposes, the SNA service contains two local LUs paired together (for invoking and invokable TPs that are in the same domain). In this situation, a connection to a host or peer is not necessary.  
  
- The partner LU alias specified in the symbolic destination name must match an LU alias that is paired with the local LU alias used by the invoking TP.  
  
  The preceding parameters support the beginning of the invoking process. For the invoking process to successfully complete, additional parameters must be configured as described in [Invokable TPs and the SNA Service Configuration](../core/invokable-tps-and-the-sna-service-configuration-cpi-c-1.md).