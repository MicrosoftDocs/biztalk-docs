---
title: "Troubleshooting for Invokable TPs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 39624cee-4f95-49a0-9358-53e1d4383252
caps.latest.revision: 3
---
# Troubleshooting for Invokable TPs
If there are difficulties with starting an invokable TP, there may be a mismatch between the information for the invokable TP, the invoking TP, and/or LUs in the [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] configuration. That is, there may be a mismatch between the parameters for [RECEIVE_ALLOCATE](../core/receive-allocate2.md), [TP_STARTED](../core/tp-started1.md), [ALLOCATE](../core/allocate1.md), or [MC_ALLOCATE](../core/mc-allocate1.md) and/or LU aliases specified in server configuration. LU aliases are configured using SNA Manager on [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)].  
  
## Simplifying APPC Configuration  
 There are several features in [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] that can simplify configuration for APPC:  
  
-   The implicit incoming remote LU and the implicit incoming mode, which allow Host Integration Server to accept requests that arrive by unrecognized remote LUs and modes.  
  
-   The default local APPC LU and the default remote APPC LU, which allow LU aliases to be associated with user or group names, simplifying the routing of incoming requests and the configuration of client systems.  
  
-   The default outgoing local APPC LU pool, which allows LUs to be allocated dynamically to any invoking TP that does not specify a local LU.  
  
-   Automatic partnering, which automatically creates LU-LU pairs and assigns modes to the pairs.