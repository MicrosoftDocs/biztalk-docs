---
description: "Learn more about: Troubleshooting for Invokable TPs"
title: "Troubleshooting for Invokable TPs2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Troubleshooting for Invokable TPs
If there are difficulties with starting an invokable TP, there may be a mismatch between the information for the invokable TP, the invoking TP, and/or LUs in the Host Integration Server configuration. That is, there may be a mismatch between the parameters for [RECEIVE_ALLOCATE](./receive-allocate1.md), [TP_STARTED](./tp-started2.md), [ALLOCATE](./allocate2.md), or [MC_ALLOCATE](./mc-allocate2.md) and/or LU aliases specified in server configuration. LU aliases are configured using SNA Manager on Host Integration Server.  
  
## Simplifying APPC Configuration  
 There are several features in Host Integration Server that can simplify configuration for APPC:  
  
-   The implicit incoming remote LU and the implicit incoming mode, which allow Host Integration Server to accept requests that arrive by unrecognized remote LUs and modes.  
  
-   The default local APPC LU and the default remote APPC LU, which allow LU aliases to be associated with user or group names, simplifying the routing of incoming requests and the configuration of client systems.  
  
-   The default outgoing local APPC LU pool, which allows LUs to be allocated dynamically to any invoking TP that does not specify a local LU.  
  
-   Automatic partnering, which automatically creates LU-LU pairs and assigns modes to the pairs.
