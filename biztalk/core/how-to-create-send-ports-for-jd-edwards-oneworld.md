---
title: "How to Create Send Ports for JD Edwards OneWorld | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating send ports"
  - "send ports, creating"
ms.assetid: 858425ef-bdb7-4d2d-90ca-b3655e389749
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create Send Ports for JD Edwards OneWorld
Use the following procedure to create a send port.  
  
### To create a send port  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then navigate to the required application.  
  
2.  Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.  
  
    > [!NOTE]
    >  You can also use **Static One-Way Port**.  
  
3.  In the **Send Port Properties** dialog box, in the **Name** field, type a send port name (for example, type **SendToJDE**.)  
  
4.  In the **Type** drop-down list, select **JDEOneWorld**.  
  
5.  In the **URI** drop-down list, select the send handler.  
  
6.  Click **OK**.  
  
## See Also  
 [Creating JD Edwards OneWorld Send Handlers](../core/creating-jd-edwards-oneworld-send-handlers.md)