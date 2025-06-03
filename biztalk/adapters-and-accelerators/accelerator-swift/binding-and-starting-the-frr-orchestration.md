---
description: "Learn more about: Binding and Starting the FRR Orchestration"
title: "Binding and Starting the FRR Orchestration"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Binding and Starting the FRR Orchestration
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] includes the FRR orchestration as a deployed assembly (Microsoft .Solutions.FinancialServices.SWIFT.FrrOrchestration). You need to start this orchestration.  
  
 **Summary**  
  
 To start the FRR orchestration, do the following:  
  
-   Bind the FrrOrchestration.FrrMain orchestration by setting the host to BizTalkServerApplication.  
  
-   Start the FrrOrchestration.FrrMain orchestration.  
  
### To bind and start the FRR orchestration  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and then **BizTalk Application 1**. Click **Orchestrations**.  
  
2.  In the Orchestrations pane, right-click the **FrrOrchestration.FrrMain** orchestration, and then click **Properties**.  
  
3.  In the Orchestration Properties dialog box, click **Bindings** in the left pane. For **Host**, select **BizTalkServerApplication**. Click **Apply**, and then click **OK**.  
  
4.  In the Orchestrations pane, right-click the **FrrMain** orchestration, and then click **Start**.
