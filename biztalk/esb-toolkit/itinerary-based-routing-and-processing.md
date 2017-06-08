---
title: "Itinerary-Based Routing and Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8354538-e45c-487d-a380-59f497ea060f
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Itinerary-Based Routing and Processing
The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] implements a routing slip pattern through the use of custom pipeline components. Message metadata and other factors are used to determine the appropriate routing slip, also known as an itinerary, to be used for each message. This routing slip can perform message transformation, invoke orchestration services, and define message routing steps that [!INCLUDE[prague](../includes/prague-md.md)] will execute, effectively decoupling message processing instructions from the core BizTalk Server engine.  
  
 For more information on how itineraries are processed, see [Key Scenarios and Development Tasks](../esb-toolkit/key-scenarios-and-development-tasks.md).