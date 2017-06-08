---
title: "How to Set JD Edwards OneWorld Pipelines | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive pipelines"
  - "send pipelines"
  - "setting pipelines"
  - "pipelines, setting"
ms.assetid: 821d4081-a2d4-4957-abc0-d6370e719ba8
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set JD Edwards OneWorld Pipelines
Microsoft BizTalk Adapter for JD Edwards OneWorld requires that you select XMLTransmit and XMLReceive for the send and receive pipelines respectively.  
  
### To set pipelines  
  
1.  On the **Start** menu, point to **Program Files**, point to **Microsoft BizTalk Server** , and then click **BizTalk Server Administration** to start the BizTalk Server Administration Console.  
  
2.  Expand BizTalk Server Administration, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.  
  
3.  Select **Send Ports**. In the details pane, right-click the selected send port and click **Properties**.  
  
4.  In the **Send Ports Properties** dialog box, do the following:  
  
    1.  Select the send pipeline from the **Send Pipeline** drop-down list.  
  
    2.  Select the Receive pipeline from the **Receive Pipeline** drop-down list.  
  
5.  Click **OK**.  
  
## See Also  
 [Creating JD Edwards OneWorld Send Handlers](../core/creating-jd-edwards-oneworld-send-handlers.md)