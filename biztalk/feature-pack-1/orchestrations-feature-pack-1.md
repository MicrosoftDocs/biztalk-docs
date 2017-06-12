---
title: "Orchestrations (Feature Pack 1) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 419bb9d1-3c7f-40e8-95d3-8a3d4464761c
caps.latest.revision: 8
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Orchestrations (Feature Pack 1)
Managing Feature Pack 1 can be accomplished through a REST interface.  

Common tasks
---

**Orchestrations**
- get  /Orchestrations [Get all Orchestrations](../feature-pack-1/get-all-orchestrations.md)
- put  /Orchestrations [Update Orchestration. Allows us to Bind/Unbind Ports, Host and Change Tracking Options](../feature-pack-1/update-orchestration.md)
- get  /Orchestrations/{applicationName}/{orchestrationName} [Get Specific Orchestration](../feature-pack-1/get-specific-orchestration.md)
- put  /Orchestrations/{applicationName}/{orchestrationName}/Enlist [Enlist Orchestration](../feature-pack-1/enlist-orchestration.md)
- put  /Orchestrations/{applicationName}/{orchestrationName}/Unenlist [Unenlist Orchestration](../feature-pack-1/unenlist-orchestration.md)
- put  /Orchestrations/{applicationName}/{orchestrationName}/Start [Start Orchestration](../feature-pack-1/start-orchestration.md)
- put  /Orchestrations/{applicationName}/{orchestrationName}/Stop [Stop Orchestration](../feature-pack-1/stop-orchestration.md)
