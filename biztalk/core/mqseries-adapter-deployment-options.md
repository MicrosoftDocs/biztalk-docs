---
description: "Learn more about: MQSeries Adapter Deployment Options"
title: "MQSeries Adapter Deployment Options"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
