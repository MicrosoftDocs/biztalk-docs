---
title: "Role of the Base (SNADIS)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81a950dc-1af9-4940-937f-e6232ba00c74
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Role of the Base (SNADIS)
TheBase is a part of each [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] component, such as the local 2.1 node or a link service that provides the operating environment for that component. It passes messages between components and provides functions common to all components, such as diagnostic tracing.  
  
 The Link Base is the type of Base used by Host Integration Server SNALink. The Base has entry points for initialization, sending messages, receiving messages, and termination.