---
title: "How to Configure an MSMQ Receive Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive handlers, MSMQ adapters"
  - "configuring [MSMQ adapters], receive handlers"
  - "MSMQ adapters, receive handlers"
ms.assetid: d6d82098-3a73-44e2-80d5-143f77e919cc
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure an MSMQ Receive Handler
Use the following procedure to change the host with which the MSMQ receive handler is associated.  
  
> [!NOTE]
>  Each host can associate with only one receive handler.  
  
### To change the host with which the MSMQ receive handler is associated  
  
1.  In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  
  
2.  In the expanded adapter list, click **MSMQ**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.  
  
3.  In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.  
  
4.  Click **OK**.  
  
## See Also  
 [Configuring the MSMQ Adapter](../core/configuring-the-msmq-adapter.md)