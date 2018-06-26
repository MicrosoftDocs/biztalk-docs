---
title: "TPs with Explicit SYNCPOINT Commands2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 602a14c9-84b6-4eae-88ed-db1200c18958
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TPs with Explicit SYNCPOINT Commands
CICS LU 6.2 Link transaction programs (TPs) cannot use explicit EXEC SYNCPOINT commands to control the transaction semantics of COM+ transactions. However, if an existing CICS Link TP does issue explicit EXEC SYNCPOINT commands, you do not need to modify the TP to have it work successfully with TI. You need only meet the following two requirements for TI components that execute within the transaction.  
  
-   Set the TI component's transaction property to **Does not support transactions**. You define a component's transaction property when you create the component in TI Designer. Once you deploy the TI component in a COM+ application, you can view or modify its transaction property in TI Manager.  
  
-   Configure the remote environment (RE) that describes the region on the mainframe and that hosts the CICS Link TP to allow the use of explicit SYNCPOINT commands for non-transactional components.  
  
### To configure the RE to allow the use of explicit SYNCPOINT commands  
  
1. In TI Manager, right-click the RE that you want to configure, click **Properties**, and then click the **CICS Mirror TP** tab.  
  
2. Select the **Allow use of explicit SYNCPOINT commands for nontransactional components** check box.  
  
3. Click OK.  
  
   If the two requirements are not met, the transaction will not work on either the Windows or the mainframe side. In which case, TI writes a message to the Windows Event Log explaining the cause of the failure.  
  
## See Also  
 [WIP Programming Model](../core/wip-programming-model2.md)