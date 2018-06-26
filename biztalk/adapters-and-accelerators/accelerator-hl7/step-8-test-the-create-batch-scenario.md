---
title: "Step 8: Test the Create-Batch Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc7fac40-fd3e-413b-82cc-7ad08226094c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 8: Test the Create-Batch Scenario
In this step, you test the Create-Batch scenario by dropping test instances of the messages you want to batch into the source Tutorial_BTAHL7Pickup folder. The send port that you set up picks up the message from the source folder and sends it; the receive port receives it; and the receive pipeline processes it and drops it into the destination Tutorial_BTAHL7Drop folder.  

### To test the Create-Batch scenario  

1. Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\Batching Tutorial\Instances** folder.  

2. Select **CreateBatchMessage1.txt**, and **CreateBatchMessage2.txt**, right-click them, and then click **Copy**.  

3. Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Pickup** folder.  

4. Right-click the folder, and then click **Paste**.  

### To verify the results of the Create-Batch scenario  

1. Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BatchACKDrop** folder. After a short period, you should see the processed instance of the acknowledgment batch appear in the folder. If it does not appear, check the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer for error messages. The file should have the name \<*Guid*\>.txt. This batch should contain the two acknowledgments generated upon receiving the two messages that were originally sent. This batch should have the following fields:  

   |FHS.5|BHS.5|BTS.1|FTS.1|  
   |-----------|-----------|-----------|-----------|  
   |Tutorial_BatchSource|Tutorial_BatchSource|2|1|  

    The acknowledgments within the batch should have the following fields:  


   |    MSH.9    | MSA.2 | MSA.1 |       MSH.3        |        MSH.5         |
   |-------------|-------|-------|--------------------|----------------------|
   | ACK^A03^ACK | Msg01 |  AA   | Tutorial_BatchDest | Tutorial_BatchSource |
   | ACK^A03^ACK | Msg02 |  AA   | Tutorial_BatchDest | Tutorial_BatchSource |


2. Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BatchMsgDrop** folder. After an hour, you should see the processed instance of the message batch appear in the folder. If it does not appear, check the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer for error messages. The file should have the name \<*Guid*\>.txt. This batch should contain the two messages that were originally sent. This batch should have the following fields:  

   |FHS.5|BHS.5|BTS.1|FTS.1|  
   |-----------|-----------|-----------|-----------|  
   |Tutorial_BatchDest|Tutorial_BatchDest|2|1|  

    The messages within the batch should have the following fields:  

   |MSH.9|MSH.10|MSH.3|MSH.5|  
   |-----------|------------|-----------|-----------|  
   |ADT^A03|Msg01|Tutorial_BatchSource|Tutorial_BatchDest|  
   |ADT^A03|Msg02|Tutorial_BatchSource|Tutorial_BatchDest|  

    The batch is wrapped in two sets of headers and trailers specific to batches:  

   -   A file header and trailer (FHS and FTS), which are used to enclose a file that can include multiple batches. Note the file-receiving application (**Tutorial_BatchDest**) in the FHS5 field and the file creation date/time in FHS7. Note the file batch count (the number of batches in the file) in FTS2 (1).  

   -   A batch header and trailer (BHS and BTS), which are used to enclose each batch. Note the file receiving application and batch creation date/time, as in the FHS, and the batch message count (2) in BTS2.  

## See Also  
 [Part 1: Fragmented Inbound Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)   
 [Part 3: Create-Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)