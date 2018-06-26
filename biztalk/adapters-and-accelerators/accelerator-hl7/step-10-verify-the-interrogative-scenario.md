---
title: "Step 10: Verify the Interrogative Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interrogative tutorial, verifying solution"
ms.assetid: 1f28800b-4a1d-4f29-8123-5cdea4b4a365
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 10: Verify the Interrogative Scenario
In this step, you verify the end-to-end scenario for this tutorial.  
  
### To send the query message  
  
1.  Open a command prompt.  
  
2.  In the command prompt, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**.  
  
3.  In the command prompt, type **MllpReceive /P 24000**, and then press **Enter**. This runs the MLLP listener application listening to port 24000 and displays any messages received to the screen. This application is simulating the Hospital Information System.  
  
4.  Open an additional command prompt.  
  
5.  In the second Command Prompt window, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**.  
  
6.  In the second command prompt, type **MllpSend /SB 11 /EB 28 /CR 13 /TWOWAY /P 22000 /F "\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial\QRY^Q01.txt**, and then press **Enter.**  
  
    > [!NOTE]
    >  This command sends the query message you created at the beginning of this tutorial to MLLP port 22000 and waits for a response (acknowledgment). The ADT receive port picks up this message and processes it.  
  
7.  Verify that you have the following results:  
  
    -   The MLLP listener application should display a message with the following values:  
  
        ```  
        MSH|^~\&|ADT||HIS||19990303||QRY^Q01|MSG00001|P|2.4  
        QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
        ```  
  
    -   In addition, the MllpSend utility creates an acknowledgment file in the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial folder named QRY^Q01.txt.RESPONSE. This file contains the following information as the acknowledgment:  
  
        ```  
        MSH|^~\&|HIS||ADT||20040331154031.2222-0800||ACK^Q01^ACK|10000GSM|P|2.4  
        MSA|CA|MSG00001  
        ****END ACK****  
        ```  
  
### To send the response message  
  
1. In the command prompt running the MllpReceive application, press **Ctrl-C** to cancel the previous operation.  
  
2. At the command prompt, type **MllpReceive /P 25000**, and then press **Enter**.  
  
   > [!NOTE]
   >  Step 2 runs the MLLP listener application listening to port 25000 and displays any messages received to the screen. This application is simulating the ADT system.  
  
3. In the second command prompt, type **MllpSend /SB 11 /EB 28 /CR 13 /P 23000 /F "\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial\DSR.txt"**, then press **Enter**.  
  
   > [!NOTE]
   >  Step 3 sends the response message you created at the beginning of this tutorial to MLLP port 23000. The HIS receive port picks up this message and processes it.  
  
4. Verify that you have the following results:  
  
   -   The MLLP listener application should display a message with the following values:  
  
       ```  
       MSH|^~\&|HIS||ADT||19990505||DSR^Q01|ZXT23469|P|2.4  
       MSA|AA|MSG00003  
       QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
       DSP|||RESULTS FOR PATIENT#12233 SMITH, JOHN H. 07/23/03  
       DSP|||SPECIMEN#H85 COLLECTED 07/22/03 /07/0/0  
       DSP|||ELECTROLYTES  
       DSP||| SODIUM 136 [135-148] MEQ/L STAT  
       DSP||| POTASSIUM 4.2 [3.5-5.0] MEQ/L STAT  
       DSP||| CHLORIDE 91 [95-111] MEQ/L STAT  
       DSP||| CO2 25 [20-30] MEQ/L STAT  
       DSP|||CO2 25 [20-30] MEQ/L STAT|LB  
       ```  
  
   > [!NOTE]
   >  If the messages above do not appear correctly, use the Health and Activity Tracking (HAT) tool to troubleshoot the error.  
  
   Congratulations! You have successfully completed the BTAHL7 Interrogative Tutorial.  
  
## See Also  
 [Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)   
 [End-to-End Tutorial](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)   
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)