---
title: "How to Set Send Pipelines for TIBCO Enterprise Message Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send pipelines"
  - "setting send pipelines"
  - "pipelines, send"
ms.assetid: 6a84d874-4b4d-4b23-913f-f5c72af1e96e
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set Send Pipelines for TIBCO Enterprise Message Service
Microsoft BizTalk Adapter for TIBCO Enterprise Message Service requires that you select XMLTransmit and XMLReceive for the Send and Receive pipelines respectively.  
  
### To set pipelines  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.  
  
2.  Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.  
  
3.  In the **Send Port Properties** dialog box, do the following:  
  
    1.  Type a name for the send port, for example, `SendToTIBCOEMS`.  
  
    2.  From the **Type** drop-down list, select **TIBCO EMS**.  
  
    3.  From the **Send handler** drop-down list, select the URI.  
  
    4.  From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
4.  Click **OK**.  
  
## See Also  
 [How to Set Receive Pipelines for TIBCO Enterprise Message Service](../core/how-to-set-receive-pipelines-for-tibco-enterprise-message-service.md)