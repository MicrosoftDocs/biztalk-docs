---
title: "Step 9: Test the EDI Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7a44e0f-496c-462f-bf03-1c2f842d13b6
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 9: Test the EDI Solution
![Step 9 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")  
  
 In this topic you test your inbound processing and view the EDI-Interchange Status Report for processing information.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### Testing the solution  
  
1. In Windows Explorer, move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations. Copy the **SamplePO.txt** file.  
  
2. Paste the **SamplePO.txt** file into the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\fromTHEM folder.  
  
3. Move to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toOrderSystem folder. Confirm that the folder contains an output txt file.  
  
4. Open the output file in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toOrderSystem and the SamplePO.txt input file in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations. Verify that the data in the output message corresponds to the data in the original **SamplePO.txt** file.  
  
   > [!NOTE]
   >  You can verify that the data in the output file has been transformed from the data in the input file by opening the Inbound4010850_to_OrderFile.btm file in Visual Studio, and checking the mappings.  
  
5. Move to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toTHEM_997 folder. Confirm that the folder contains an output 997 acknowledgment txt file in which the ST01 data element is "997".  
  
6. In the console tree of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **BizTalk Group**. At the bottom of the right pane, click **EDI Interchange and Correlated ACK Status**.  
  
7. In the query expression, change the operator for the **Status** field to **Equals** and change the **Value** field for the **Status** field to **All**. Delete the **Interchange Date Time field** (select the row and press DELETE on the key board).  
  
8. Click **Run Query**.  
  
9. Verify that two messages are displayed in the status report, one in the receive direction from THEM (Fabrikam) to US (OrderSystem) (the 850 message), the other in the send direction from the US (OrderSystem) to THEM (Fabrikam) (the 997 acknowledgment).  
  
10. Double-click the message from THEM to US. In the **Interchange status and ACK  details** dialog box, verify that details of the interchange are displayed in the right pane.  
  
11. Click **Functional ACK(s)**. Verify that the report details of the acknowledgment are displayed in the right pane.  
  
12. Close the Interchange status and ack details dialog box.  
  
13. In the **Interchange/ACK Status** pane, right-click the message from THEM to US, and then click **Transaction Set Details**. Right-click the entry in the **Query results** pane, and then click **View Transaction Set Content**. Verify that the transaction set data is displayed in the **Message Details** dialog box. In Windows Explorer, open the SamplePO.txt file in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\ProcessEDI_TestLocations. Verify that the transaction set displayed in the **Message Details** dialog box is the same as that in the input message, without the interchange and group headers and trailers.  
  
## Next Steps  
 You have completed the EDI Interface Developer Tutorial.  
  
## See Also  
 [Tutorial 2: EDI Interface Developer Tutorial](../core/tutorial-2-edi-interface-developer-tutorial.md)   
 [Step 1: Prepare for the EDI Interface Developer Tutorial](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)