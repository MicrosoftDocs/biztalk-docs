---
title: "Making Connections (SNADIS)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6182dde5-5348-4d57-829d-7941012c023a
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Making Connections (SNADIS)
Before messages can flow across connections, the connections must be established, or opened. This is necessary because a service does not initially know the locality, partner, index (LPI) address of the service with which it wants to communicate. There may not even be a suitable service for it to communicate with.  
  
 When a local node wants to communicate with an SNALink, it attempts to open a connection by sending an **Open(LINK)** request to the SNALink. This message will have LPI values already set up by the Base, which the SNALink should save for referencing the connection in the future.  
  
 The data link control (DLC) interface does not permit the SNALink to issue an Open request.