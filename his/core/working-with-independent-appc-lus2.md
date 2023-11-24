---
description: "Learn more about: Working with Independent APPC LUs"
title: "Working with Independent APPC LUs2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Working with Independent APPC LUs
An independent LU can communicate directly with a peer system and does not need the support of a host computer. Independent APPC LUs, as used in IBM System i APPN networks, provide the ability to run multiple, concurrent, parallel sessions between a local and remote LU pair.  
  
 When configuring independent APPC LUs, you should note that when Host Integration Server is used to communicate with a transaction program (TP) on a mainframe over an independent APPC LU, the host system must be running VTAM version 3, release 2 (V3R2) or later. The version of Network Control Program (NCP) required on the mainframe depends on the type of front-end processor (FEP) used. For 3725 systems, NCP V4R3 or later is required. For 3745 systems, NCP V5R2 or later is required.  
  
## See Also  
 [APPC Deployment Strategies](../core/appc-deployment-strategies1.md)
