---
title: "Role of the Base (SNADIS)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3957aace-b9e5-420a-965f-91b373195a21
caps.latest.revision: 3
---
# Role of the Base (SNADIS)
TheBase is a part of each [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] component, such as the local 2.1 node or a link service that provides the operating environment for that component. It passes messages between components and provides functions common to all components, such as diagnostic tracing.  
  
 The Link Base is the type of Base used by Host Integration Server SNALink. The Base has entry points for initialization, sending messages, receiving messages, and termination.