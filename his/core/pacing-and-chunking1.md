---
title: "Pacing and Chunking1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8d26db1-aec3-4df9-aa77-7d673ee94619
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Pacing and Chunking
The local node supports session pacing inbound and outbound, according to the pacing values in the **BIND** parameters for the session. The application can be involved in outbound pacing through the use of the [Status-Resource](./status-resource1.md) message. Inbound pacing is handled transparently by the local node and need not concern the application.  
  
## In This Section  
  
-   [Outbound Pacing](../core/outbound-pacing1.md)  
  
-   [Chunking](../core/chunking2.md)