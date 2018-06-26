---
title: "Step 3: Test the Batch In-Batch Out Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c487d39d-b2be-41d4-963e-d0ee9ba169fb
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Test the Batch In/Batch Out Scenario
In this step, you test the Batch In/Batch Out tutorial by dropping a test instance of the batch in/batch out message into a folder. The send port that you set up will send the message, the receive port will receive it, and the receive pipeline will process it and drop it into the destination folder.  
  
### To test the Batch In/Batch Out scenario  
  
1. Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\Batching Tutorial\Instances** folder.  
  
2. Right click **BatchInBatchOut.txt**, and then click **Copy**.  
  
3. Browse to the **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7PickUp** folder.  
  
4. Right-click the folder, and then click **Paste**.  
  
### To verify the results of the Batch In/Batch Out Tutorial  
  
- Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop** folder. After a short period, you should see the processed instance of the batch message, and an acknowledgment, appear in the folder. If they do not appear, check the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer for an error message. Each file should have a different name in the form \<*Guid*\>.txt.  
  
   The first message should be the batch consisting of two messages. BizTalk Accelerator for HL7 (BTAHL7) has included these two messages sequentially in the .txt file. This batch does not contain FHS/FTS and BHS/BTS tags. A batch must contain either all FHS/FTS and BHS/BTS tags, or like this batch message, no FHS/FTS and no BHS/BTS tags.  
  
  |MSH.9|MSH.10|MSH.3|MSH.5|  
  |-----------|------------|-----------|-----------|  
  |ADT^A03|000001|Tutorial_BatchSource|MESA_IS|  
  |ADT^A03|000002|Tutorial_BatchSource|MESA_IS|  
  
   The second message should be a single application acknowledgment sent in response to the batch message, with the following fields:  
  
  |MSH.9|MSH.3|MSH.5|MSA.1|MSA.2|  
  |-----------|-----------|-----------|-----------|-----------|  
  |ACK^A03^ACK|MESA_IS|Tutorial_BatchSource|AA|000001|  
  
## See Also  
 [Part 1: Fragmented Inbound Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)   
 [Part 3: Create-Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)