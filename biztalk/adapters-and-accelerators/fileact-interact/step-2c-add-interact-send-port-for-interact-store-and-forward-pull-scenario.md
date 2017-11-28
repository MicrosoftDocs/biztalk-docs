---
title: "Step 2C: Add an INTERACT Send Port for the InterAct Store and Forward (Pull) Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57038f77-85c3-4811-ab3d-df6e2da8fbcf
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2C: Add an INTERACT Send Port for the InterAct Store and Forward (Pull) Scenario
Before you begin this step, you must complete [Step 2B: Add FILE Send Ports to Capture the Sw:HandleRequest Message for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md).  
  
### To add an INTERACT send port  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.  
  
4.  In the **Send Port Properties** window, name the send port, **Tutorial_IA_SendRequest_SnF**.  
  
5.  In the **Send Port Properties** window, from the **Transport type** drop-down list, select **INTERACT**, and then click **Configure**.  
  
6.  In the **INTERACT Transport Properties** dialog box, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Password**|Set the password as appropriate for SAG connectivity.|  
    |**User name**|Set the user name as appropriate for SAG connectivity.|  
    |**Message format**|**InteractMessage**|  
    |**Non-Repudiation Indicator**|**FALSE**|  
    |**Request Type**|Type the appropriate \<RequestType\> string, based on your provisioning with SWIFT.|  
    |**ResponseCrypto**|**FALSE**|  
    |**Requestor**|Type the appropriate \<RequestorDN\> string, based on your provisioning with SWIFT.|  
    |**Responder**|Type the appropriate \<ResponderDN\> string, based on your provisioning with SWIFT.|  
    |**Service Name**|Type the appropriate \<service name\>, based on your provisioning with SWIFT.|  
    |**Delivery Notification**|From the drop-down list, select **FALSE**.|  
    |**Notify queue**|Type the appropriate queue name, based on your provisioning with SWIFT.|  
  
    > [!NOTE]
    >  If only payload is to be transferred, set the MessageFormat to “Payload” in the INTERACT receive port and INTERACT send port. Set the Receive and Send pipelines to PassThru.  
  
7.  Click **OK**.  
  
8.  In the **Send Port Properties** window, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Send handler**|From the drop-down list, select the Interact host.|  
    |**Send pipeline**|From the drop-down list, select **XMLTransmit**.|  
    |**Receive pipeline**|From the drop-down list, select **XMLReceive**.|  
  
9. In the **Send Port Properties** window, on the **Filters** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Property**|From the drop-down list, select **BTS.ReceivePortName**.|  
    |**Operator**|From the drop-down list, select **==**.|  
    |**Value**|Type **Tutorial_IA_InputRequest_SnF**.|  
    |**Group by**|Leave the default value.|  
  
10. Click **OK**.  
  
## See Also  
 [Step 2A: Add FILE Receive Locations for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md)   
 [Step 2B: Add FILE Send Ports to Capture the Sw:HandleRequest Message for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md)