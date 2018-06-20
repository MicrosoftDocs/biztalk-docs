---
title: "Step 6: Configure a Send Port to Send Data to Your Organization | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 796570ca-8178-4679-9213-d67a2a189bf9
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 6: Configure a Send Port to Send Data to Your Organization
![Step 6 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-6of9.gif "Step_6of9")  

 In this step you configure a send port to send the 850 message from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to the OrderSystem party that represents your organization. This send port applies the **Inbound4010850_to_OrderFile** map, transforming the output message from the format of the input message to the format specified in the map.  

## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  

### To configure a send port for the 850 message  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Pipelines**, and then click **Refresh**.  

   > [!NOTE]
   >  Refreshing the pipelines list may be necessary to be able to select the SendOrderFilePipeline for the send port that you will create.  

2. Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

3. In the **Send Port Properties** dialog box, do the following:  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Name**|Enter `toOrderSystem`.|  
   |**Type**|Select **FILE**.|  
   |**Configure**|Click **Configure**.|  

   > [!NOTE]
   >  The transport type of the send port is FILE because the test message is a flat file to be delivered into a folder.  

4. In the **FILE Transport Properties** dialog box, do the following and then click **OK**:  


   |        Use this        |                                                                                                               To do this                                                                                                               |
   |------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Destination folder** | Click **Browse**, and in the **Browse for Folder** dialog box, move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\ Scenario A\toOrderSystem |
   |     **File name**      |                                                                                            Enter `%MessageID%.txt`, and then click **OK**.                                                                                             |

   > [!NOTE]
   >  The value set for the **File name** property ensures that the output file will have a .txt extension.  

5. In the **Send Port Properties** dialog box, for **Send pipeline**, select **SendOrderFilePipeline**.  

   > [!NOTE]
   >  The **SendOrderFilePipeline** send pipeline includes a flat-file assembler that assembles the .txt output file, using data mapped from the input 850 message. Since the output file is a .txt file, it will not show up in the Interchange/ACK status report.  

6. In the console tree, click **Filters**, and then do the following:  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Property**|Select **BTS.ReceivePortName**.|  
   |**Operator**|Select **==**.|  
   |**Value**|Enter `ReceiveEDI_fromTHEM_A`.|  
   |**Group by**|Select **And**.|  
   |**Property**|On the next line, select **BTS.MessageType**.|  
   |**Operator**|Select **!=**.|  
   |**Value**|Enter `http://schemas.microsoft.com/Edi/X12#X12_997_Root`.|  

   > [!NOTE]
   >  The filter ensures that the send port will pick up messages that were received by the Receive_EDI_fromTHEM_A receive location, and that the send port will not pick up 997 acknowledgments, but will pick only 850 messages.  

7. In the console tree, click **OutboundMaps**. In the **Outbound Maps** pane, in the **Map** column, on the first row, select **Inbound4010850_to_OrderFile**. (The entry in the **Source Document** column will be X12_00401_850.)  

   > [!NOTE]
   >  This step ensures that the output message will consist only of the data mapped from the input message according to the **Inbound4010850_to_OrderFile** map.  

8. Click **OK**.  

9. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **Send Ports**. Right-click **toOrderSystem**, and then click **Start** to enlist and start the port.  

## Next Steps  
 You configure the send port (**toTHEM_997**) to send the 997 acknowledgment back to Fabrikam, as described in [Step 7: Configure a Send Port to Send the Acknowledgment to Your Trading Partner](../core/step-7-configure-a-send-port-to-send-the-acknowledgment-to-trading-partner.md).  

## See Also  
 [Configuring a Static Send Port to Send EDI Interchanges and Acknowledgments](../core/configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments.md)