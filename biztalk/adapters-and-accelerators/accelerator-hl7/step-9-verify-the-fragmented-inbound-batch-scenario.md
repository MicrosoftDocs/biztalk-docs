---
title: "Step 9: Verify the Fragmented Inbound Batch Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ba61866-2e1b-49e2-be57-ef281407d0a5
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 9: Verify the Fragmented Inbound Batch Scenario
In this step, you verify the Fragmented Inbound Batch scenario.  
  
 Verifying the scenario involves using the following tools:  
  
- **MllpSend Tool**, which you use from the command line to send a batch message to the receive port.  
  
- **MllpReceive Tool**, which you use from the command line to verify reception of the individual messages (as contained in the batch) from the send port. This instance of the MllpReceive Tool functions as a simulated line-of-business application. On reception of the messages, it also generates an acknowledgment back to the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] integration engine.  
  
- A second instance of the MllpReceive Tool, which you use to verify reception of acknowledgments from the send port.  
  
### To test the Fragmented Inbound Batch scenario  
  
1. Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Command Prompt**.  
  
2. At the command prompt, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**.  
  
3. At the command prompt, type **mllpreceive /p 41000 /sb 11 /eb 28 /cr 13 /hl7ack "\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\Samples\Sample Application Accept ACK.txt**, and then press **Enter**. The Command Prompt window enters a waiting state until you perform step 5 and the system receives input.  
  
   > [!NOTE]
   >  The command in step 3 runs the MLLP listener application that listens to port 41000. This port is associated with the send port that delivers messages (as created in [Step 5: Create a Send Port to Deliver Messages](../../adapters-and-accelerators/accelerator-hl7/step-5-create-a-send-port-to-deliver-messages.md)). The MllpReceive Tool acts as the line-of-business application that receives the messages, and sends the acknowledgment (ACK) back to BTAHL7 (as contained in the sample file Sample Application Accept ACK.txt). The tool displays any messages returned to it in the Command Prompt window. The command in step 3 specifies the default EB, SB, and CR characters of the MLLP message.  
  
4. Repeat steps 1 and 2 to open another Command Prompt window and browse to the MLLP Utilities directory. At the command prompt, type **mllpreceive /p 41002**, and then press **Enter**. The Command Prompt window enters a waiting state until you perform step 5 and the system receives output.  
  
   > [!NOTE]
   >  The command in step 4 runs the MLLP listener application listening to port 41002. This port is associated with the send port that delivers acknowledgments back to the source of the batch message (as created in [Step 6: Create a Send Port to Deliver Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-acknowledgments.md)). The MllpReceive Tool acts as the line-of-business application that sent the original batch. The tool displays any acknowledgments returned to it in the Command Prompt window. The command in step 4 specifies the default EB, SB, and CR characters of the MLLP message.  
  
5. Repeat steps 1 and 2 to open another Command Prompt window and browse to the MLLP Utilities directory. At the command prompt, type **mllpsend /twoway /sb 11 /eb 28 /cr 13 /f "\<*drive*\>:\Batching Tutorial\Instances\FragmentedInboundBatch.txt" /p 21000**, where \<*drive*\> is your installation drive letter, and then press **Enter**.  
  
   > [!NOTE]
   >  The command in step 5 simulates sending of the original batch message to the receive port. The console should display "Sent message: 1", indicating that the MllpSend tool sent the single batch message. If it does not display "Sent message: 1", check the event viewer. Verify the text of the command entered in step 5, then troubleshoot the configuration of the send and receive ports, and the status of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and BTAHL7.  
  
### To verify the results of the Fragmented Inbound Batch Tutorial  
  
1.  Verify that after a short delay, the MllpReceive tool listening for messages on port 41000 displays the contents of the individual messages fragmented from the batch and sent to the Tutorial_BatchSource party. The contents of the two messages should be as follows:  
  
    |MSH.9|MSH.10|MSH.3|MSH.5|  
    |-----------|------------|-----------|-----------|  
    |ADT^A03|000001|Tutorial_BatchSource|MESA_IS|  
    |ADT^A03|000002|Tutorial_BatchSource|MESA_IS|  
  
2.  Verify that after a short delay, the MllpReceive tool listening for acknowledgments on port 41002 displays the contents of two acknowledgments returned from the BTAHL7 integration engine to the source of the batch. The contents of the two acknowledgments should be as follows:  
  
    |MSH.9|MSH.3|MSH.5|MSA.2|MSA.1|  
    |-----------|-----------|-----------|-----------|-----------|  
    |ACK^A03^ACK|MESA_IS|Tutorial_BatchSource|000001|AA|  
    |ACK^A03^ACK|MESA_IS|Tutorial_BatchSource|000002|AA|  
  
## See Also  
 [Part 2: Batch In/Batch Out Scenario](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)   
 [Part 3: Create-Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)