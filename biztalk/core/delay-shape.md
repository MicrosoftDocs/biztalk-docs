---
title: "Delay Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.delay"
ms.assetid: b29c5dbf-2f8b-4e26-bc1a-4f93a139846d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Delay Shape
The **Delay** shape enables you to control the timing of the progress of your orchestration. You can set a time-out on the **Delay** shape so that your orchestration pauses before resuming execution. You specify the time-out by using **System.DateTime**, which causes your orchestration to pause until the specified date or time is reached, or by using **System.TimeSpan**, which causes your orchestration to pause for the specified length of time.  
  
 For more information about **System.DateTime** and **System.TimeSpan**, see "DateTime Structure" and "TimeSpan Structure" in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Delay** property|Specify a time-out using **System.DateTime** or **System.TimeSpan** in order to create a corresponding delay in your orchestration. For example, if you specify **System.DateTime.UtcNow.AddSeconds (60)**, your orchestration will be idle for sixty seconds before proceeding.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Configure the Delay Shape](../core/how-to-configure-the-delay-shape.md)