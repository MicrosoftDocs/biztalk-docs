---
description: "Learn more about: Simplifying CPI-C Configuration (CPI-C)"
title: "Simplifying CPI-C Configuration (CPI-C)1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Simplifying CPI-C Configuration (CPI-C)
There are several features in Host Integration Server that can simplify configuration for Common Programming Interface for Communications (CPI-C):  
  
-   The implicit, incoming remote logical unit (LU) and the implicit, incoming mode which allow SNA service to accept requests that arrive by unrecognized remote LUs and modes.  
  
-   The default local Advanced Program-to-Program Communications (APPC) LU and the default remote APPC LU, which allow LU aliases to be associated with user or group names, simplifying the routing of incoming requests and the configuration of client systems.  
  
-   The default outgoing local APPC LU pool, which enables LUs to be allocated dynamically to any invoking TP that does not specify a local LU.  
  
-   Automatic partnering, which automatically creates LU-LU pairs and assigns modes to the pairs.
