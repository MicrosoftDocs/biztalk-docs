---
title: "How to Configure the Delay Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Delay shape [Orchestration Designer], configuring"
  - "Delay shape [Orchestration Designer]"
  - "Delay shape [Orchestration Designer], timeouts"
  - "Delay shape [Orchestration Designer], about Delay shape"
  - "configuring [Orchestration Designer], Delay shapes"
ms.assetid: 727be28d-932a-41d5-af3f-3ee6f7129a17
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Delay Shape
![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")  
Delay shape  
  
 There are two ways to specify the timeout for a **Delay**:  
  
- You can use **System.DateTime**, which causes your orchestration to pause until the specified date and time is reached.  
  
   System.DateTime.UtcNow.AddSeconds(60)  
  
  > [!NOTE]
  >  Delays must be expressed in Coordinated Universal Time (UTC) when using **DateTime**.  
  
- You can use **System.TimeSpan**, which causes your orchestration to pause for the specified length of time.  
  
   System.TimeSpan(0, 1, 0)  
  
  If your **Delay** shape is inside a **Listen** shape, you do not need to add a semicolon at the end of the expression.  
  
  For more information about **System.DateTime** and **System.TimeSpan**, see "DateTime Structure" and "TimeSpan Structure" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection.  
  
> [!NOTE]
>  In a multiple machines installation environment where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server are installed on separated machines, the **Delay** shape may end earlier than expected because of the times on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] machines are unsynchronized.  
> 
> [!NOTE]
>  Under the stress condition, the timeout specified in the **Delay** shape may occur later than what you have specified. This is because of the thread starvation under the stress condition.  
  
### To configure a Delay shape  
  
1.  If BizTalk Expression Editor is not visible, right-click the **Delay** shape and click **Edit Delay**, or in the Properties window, click the **Ellipsis** (**...**) button for the **Expression** property.  
  
2.  In BizTalk Expression Editor, create an expression that returns a **System.DateTime** object or a **System.TimeSpan** object. For more information, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md).