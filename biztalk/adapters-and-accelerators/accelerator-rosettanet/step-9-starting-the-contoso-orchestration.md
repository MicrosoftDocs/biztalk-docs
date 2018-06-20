---
title: "Step 9: Starting the Contoso Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private process tutorial, starting orchestrations"
ms.assetid: df3ff90b-5a9f-4ae7-819a-11cb36d64ccd
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 9: Starting the Contoso Orchestration
In this step, you complete the port configuration process by defining the physical source and destination locations. You bind the physical ports to the logical ports you created in [Step 7: Creating and Configuring Ports](../../adapters-and-accelerators/accelerator-rosettanet/step-7-creating-and-configuring-ports.md). You then enlist the service to associate the business process that you designed in the orchestration with the physical environment that the orchestration will run in. Finally, you start the orchestration so that it can participate in business transactions with Fabrikam.  
  
### To bind the orchestration ports  
  
1.  Open **BizTalk Explorer**.  
  
2.  In BizTalk Explorer, expand **BizTalk Configuration Database**, expand **Orchestrations**, right-click **ContosoPriceAndAvailability.PrivateResponderProcess**, and then click **Bind**.  
  
3.  On the Port Bindings Properties page, select **LOB_To_PrivateResponder** in the **FromLOB** property.  
  
4.  In the **ContosoSQLReqResponsePort** box, select **3A2SQLReqResponseSendPort**.  
  
5.  In the **ToLOB** property, expand **Send Ports** and select **PrivateResponder_To_LOB**.  
  
6.  In the Configuration window in the left pane, select **Host**.  
  
7.  In the **Host** property, in the **BizTalk Host** category, select **BizTalkServerApplication** from the drop-down list, and then click **OK**.  
  
### To start the BizTalk runtime process  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] and then click **BizTalk Server Administration**.  
  
2. In the BizTalk Administration Console, in the left pane, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Host Instances**.  
  
3. Verify that the status of the **BizTalkServerApplication** service is **Running**.  
  
### To enlist and start the orchestration  
  
1.  In the left pane of the BizTalk Administration Console, expand **Applications**, expand **BizTalk Application 1**, and then click **Orchestrations**.  
  
2.  In the right pane, right-click the **ContosoPriceAndAvailability.PrivateResponderProcess** orchestration, and then click **Enlist**.  
  
3.  Right-click the **ContosoPriceAndAvailability.PrivateResponderProcess** orchestration, and then click **Start** to start the orchestration.  
  
## See Also  
 [Creating the Fabrikam Solution](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-fabrikam-solution.md)