---
description: "Learn more about: Step 16: Start the Orchestration"
title: "Step 16: Start the Orchestration"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: article
---
# Step 16: Start the Orchestration
In this step, you enlist the service in order to associate the business process that you designed in the orchestration with the physical environment in which the orchestration will run. Additionally, you start the processing of the orchestration so that you can test your application.  
  
### To start the orchestration  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, in the console tree pane, under **Orchestrations**, right-click **BTAHL7_Project.Doorbell_Orchestration**, and then click **Enlist**.  
  
2. Right-click **BTAHL7_Project.Doorbell_Orchestration**, and then click **Start**.  
  
   > [!NOTE]
   >  Ensure that you have started the **MLLPSendPort** send port and enabled the **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort** receive location.  
  
   Proceed to [Step 17: Create the WSClient Application](../../adapters-and-accelerators/accelerator-hl7/step-17-create-the-wsclient-application.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)
