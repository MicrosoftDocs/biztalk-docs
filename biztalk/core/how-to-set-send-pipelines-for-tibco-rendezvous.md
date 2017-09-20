---
title: "How to Set Send Pipelines for TIBCO Rendezvous | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send pipelines"
  - "pipelines, send"
ms.assetid: a28a02c1-6f30-4749-b819-c1e707757680
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set Send Pipelines for TIBCO Rendezvous
Microsoft BizTalk Adapter for TIBCO Rendezvous requires that you select XMLTransmit and XMLReceive for the send and receive pipelines respectively.  
  
### To set pipelines  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.  
  
2.  Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.  
  
3.  In the **Send Port Properties** dialog box, do the following:  
  
    1.  Type a name for the send port, for example, `SendToTIBCORV`.  
  
    2.  From the **Type** drop-down list, select **TIBCO Rendezvous**.  
  
    3.  From the **Send handler** drop-down list, select the URI.  
  
    4.  From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
4.  Click **OK**.  
  
## See Also  
 [Creating TIBCO Rendezvous Send Handlers](../core/creating-tibco-rendezvous-send-handlers.md)   
 [Creating TIBCO Rendezvous Receive Handlers](../core/creating-tibco-rendezvous-receive-handlers.md)