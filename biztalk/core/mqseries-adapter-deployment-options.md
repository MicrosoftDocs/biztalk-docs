---
title: "MQSeries Adapter Deployment Options | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MQSeries adapters, deploying"
  - "deploying, MQSeries adapters"
ms.assetid: d9380aff-40ea-419b-88e2-1e2ec3f023cb
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MQSeries Adapter Deployment Options
The MQSeries adapter gives you great flexibility in configuring your hardware. There are at least three main patterns of use:  
  
-   BizTalk Server, the adapter, and MQSeries Server for Windows on the same computer.  
  
-   BizTalk Server and the adapter on one computer, and MQSeries Server for Windows (including the MQSAgent) on a second computer, which connects to one or more additional computers that are running MQSeries Server.  
  
-   Multiple BizTalk Server installations in a group and the adapter, and MQSeries Server (including MQSAgent) on a separate computer.  
  
-   The adapter functions correctly if you cluster MQSeries Server and the MQSeries Queue Managers.  
  
    > [!NOTE]
    >  The MQSAgent COM+ application should not be clustered in this case. Instead, both nodes of the cluster should have the MQSAgent COM+ application installed and configured. In this scenario, if the MQSAgent COM+ application stops, the next call from the client will restart it.  
  
## See Also  
 [Using the MQSeries Adapter](../core/using-the-mqseries-adapter.md)