---
title: "Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9522386-e980-4ab1-b65a-939ca7936ad9
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario
Complete [Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) before you begin this step.
  
## Add an INTERACT send port  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.  
  
4.  In the **Send Port Properties** window, name the send port **Tutorial_IA_SendRequest_RealTime**.  
  
5.  In the **Send Port Properties** window, from the **Transport type** drop-down list, select **INTERACT**, and then click **Configure**.  
  
6.  In the **INTERACT Transport Properties** dialog box, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Password**|Set the password as appropriate for SAG connectivity.|  
    |**User name**|Set the user name as appropriate for SAG connectivity.|  
    |**Adapter Mode**|From the drop-down list, select **RealTime**.|  
    |**Message format**|**InteractMessage**.|  
    |**Non-Repudiation Indicator**|**FALSE**.|  
    |**Request Type**|Type the appropriate \<RequestType> string, based on your provisioning with SWIFT.|  
    |**ResponseCrypto**|**FALSE**.|  
    |**Requestor**|Set it to the appropriate \<Requestor> string, based on your provisioning with SWIFT.|  
    |**Responder**|Set it to the appropriate \<Responder> string, based on your provisioning with SWIFT.|  
    |**Service Name**|Set it to the appropriate \<service name>, based on your provisioning with SWIFT.|  
    |**Delivery Notification**|From the drop-down list, select  **FALSE**.|  
    |**Notify queue**|Type the appropriate queue name, based on your provisioning with SWIFT.|  
  
    > [!NOTE]
    >  If only payload is to be transferred, set the MessageFormat to “Payloadonly” in the INTERACT receive port and INTERACT send port. Set the receive and send pipelines to PassThru.  
  
7.  Click **OK**.  
  
8.  In the **Send Port Properties** window, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Send handler**|From the drop-down list, select the Interact host.|  
    |**Send pipeline**|From the drop-down list, select **XMLTransmit**.|  
    |**Receive pipeline**|**XMLReceive**|  
  
9. In the **Send Port Properties** window, on the **Filters** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Property**|From the drop-down list, select **BTS.ReceivePortName**.|  
    |**Operator**|From the drop-down list, select **==**.|  
    |**Value**|Type **Tutorial_IA_InputRequest_RealTime**.|  
    |**Group by**|Leave the default value.|  
  
10. Click **OK**.  
  
## See Also  
 [Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md)   
 [Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md)   
 [Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md)   
 [Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md)