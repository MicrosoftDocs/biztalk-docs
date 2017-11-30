---
title: "Deployment Model | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b13357ae-020d-4ba7-954f-8d7e07f5a768
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deployment Model
Lastly where the server will be deployed will also factor into the capacity planning.  If your servers are centrally located in the data center then a core set of servers can service all the branch locations.  If your servers are branch deployed, then generally they would only service the sessions at that branch.  Typically branch deployment requires more total servers at lower capacity, where as the central deployment can use less servers at a higher capacity.  With the per CPU license model these two deployment models may not affect the over licensing cost (e.g. 4 quad-proc servers vs. 16 single-proc servers).