---
title: "Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8743a868-9625-477b-a7da-673bfa262723
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario
Before you begin this step, you must complete [Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md).  
  
### To add a FileACT send port  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.  
  
4.  In the **Send Port Properties** window, name the send port, **Tutorial_FA_SendRequest_SnF**.  
  
5.  In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILEACT**, and then click **Configure**.  
  
6.  In the **FILEACT Transport Properties** dialog box, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Password**|Set the password as appropriate for SAG connectivity.|  
    |**User name**|Set the user name as appropriate for SAG connectivity.|  
    |**Adapter Mode**|From the drop-down list, select **Store and Forward**.|  
    |**Non-Repudiation Indicator**|From the drop-down list, select **FALSE**.|  
    |**Request Type**|Set to the appropriate \<RequestType\> string, based on your provisioning with SWIFT.|  
    |**RequestCrypto**|From the drop-down list, select **FALSE**.|  
    |**Requestor**|Set to the appropriate \<Requestor\> string, based on your provisioning with SWIFT.|  
    |**Responder**|Set to the appropriate \<Responder\> string.|  
    |**Service Name**|Set to the appropriate **\<service name\>**.|  
    |**Acknowledgement Indicator**|From the drop-down list, select **FALSE**.|  
    |**Event end-point**|From the drop-down list, select **FALSE**.|  
    |**File Compression**|From the drop-down list, select **None**.|  
    |**Physical Folder Name**|Type C:\SWIFTAdapterTutorial\Fileact\ClientLocation.|  
    |**Transfer end-point**|Type the appropriate end-point for the SAG routing set. This value should match the SNL endpoint you configured in SAG.|  
    |**ServiceProfile**|From the drop-down list, select **Transaction Count**.|  
    |**Delivery notification**|From the drop-down list, select **FALSE**.|  
    |**Notify queue**|Type the queue name, based on your provisioning with SWIFT.|  
  
    > [!NOTE]
    >  If message with Transaction Count is to be transferred, set the Service Profile Mode to “Transaction Count” in the FileAct send port.  
  
7.  Click **OK**.  
  
8.  In the **Send Port Properties** window, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Send handler**|From the drop-down list, select the **FileActHost**.|  
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
 [Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md)   
 [Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md)