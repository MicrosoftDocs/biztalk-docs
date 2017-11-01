---
title: "Process Structure and Scheduling2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10265606-86aa-4a51-bdbb-0fca8fd8f2e9
caps.latest.revision: 3
---
# Process Structure and Scheduling
The primary thread of execution within a [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] SNALink is under the complete control of the Base. The Base schedules the SNALink by calling predefined entry points, which the IHV link support code must provide.  
  
 The IHV link support code can spawn extra threads of execution; however, the Base is not reentrant. The IHV code must ensure that only a single thread is executing within the Base at any moment in time.  
  
 The recommended SNALink structure uses the dispatcher to handle messages received from the local node and the work manager to process data received from the link. These routines and the way in which they are scheduled are described in [The Dispatcher](../core/dispatcher-snadis.md) and [The Work Manager](../core/work-manager.md) respectively.