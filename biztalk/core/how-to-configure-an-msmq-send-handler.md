---
description: "Learn more about: How to Configure an MSMQ Send Handler"
title: "How to Configure an MSMQ Send Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSMQ adapters, send handlers"
  - "configuring [MSMQ adapters], send handlers"
  - "send handlers, MSMQ adapters"
ms.assetid: 21917596-f27a-473b-859e-186ab5f4cd94
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure an MSMQ Send Handler
Use the following procedure to change the global variables for an MSMQ send handler.  
  
> [!NOTE]
>  Each host can have only one send handler associated with it.  
  
### To change global variables for an MSMQ send handler by using the BizTalk Server Administration console  
  
1.  In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  
  
2.  In the expanded adapter list, click **MSMQ**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.  
  
3.  In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated, and then click **Properties**.  
  
4.  In the **MSMQ Transport Properties** dialog box, enter a value for **Batch Size**.  
  
     The MSMQ send handler will send messages to destination queues using the specified **Batch Size** parameter. The default **Batch Size** value is 5.  
  
5.  Click **OK** and click **OK** again to close the **Adapter Handler Properties** dialog box.
