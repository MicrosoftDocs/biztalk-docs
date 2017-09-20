---
title: "How to Set Send Pipelines for JD Edwards EnterpriseOne | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JD Edwards EnterpriseOne adapters, send pipelines"
  - "send pipelines, configuring [JD Edwards EnterpriseOne adapters]"
  - "adapters [JD Edwards EnterpriseOne adapters], configuring"
  - "adapters [JD Edwards EnterpriseOne adapters], send pipelines"
  - "JD Edwards EnterpriseOne adapters, configuring"
ms.assetid: 4cfcecc1-febe-47c8-b75f-2b84defcdbbc
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set Send Pipelines for JD Edwards EnterpriseOne
Microsoft BizTalk Adapter for JD Edwards EnterpriseOne requires that you select **XMLTransmit** and **XMLReceive** for the send and receive pipelines respectively.  
  
### To set pipelines  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.  
  
2.  Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.  
  
3.  In the **Send Port Properties** dialog box, do the following:  
  
    1.  Type a name for the send port, for example, `SendToJDEEnterpriseOne`.  
  
    2.  From the **Type** drop-down list, select **JDE EnterpriseOne**.  
  
    3.  From the **Send handler** drop-down list, select the URI.  
  
    4.  From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
4.  Click **OK**.  
  
## See Also  
 [Creating JD Edwards EnterpriseOne Send Handlers](../core/creating-jd-edwards-enterpriseone-send-handlers.md)