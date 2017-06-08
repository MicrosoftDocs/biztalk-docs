---
title: "Binding and Starting the FRR Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FRR, binding orchestrations"
  - "FRR, starting orchestrations"
  - "bindings, orchestrations"
  - "orchestrations, bindings"
ms.assetid: b74a0116-e98b-4fec-b386-710ce421a1e2
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Binding and Starting the FRR Orchestration
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] includes the FRR orchestration as a deployed assembly ([!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.FinancialServices.SWIFT.FrrOrchestration). You need to start this orchestration.  
  
 **Summary**  
  
 To start the FRR orchestration, do the following:  
  
-   Bind the FrrOrchestration.FrrMain orchestration by setting the host to BizTalkServerApplication.  
  
-   Start the FrrOrchestration.FrrMain orchestration.  
  
### To bind and start the FRR orchestration  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and then **BizTalk Application 1**. Click **Orchestrations**.  
  
2.  In the Orchestrations pane, right-click the **FrrOrchestration.FrrMain** orchestration, and then click **Properties**.  
  
3.  In the Orchestration Properties dialog box, click **Bindings** in the left pane. For **Host**, select **BizTalkServerApplication**. Click **Apply**, and then click **OK**.  
  
4.  In the Orchestrations pane, right-click the **FrrMain** orchestration, and then click **Start**.