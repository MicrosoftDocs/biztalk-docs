---
title: "Step 18: Test Your New Message Enrichment Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message enrichment tutorial, testing solution"
ms.assetid: 233fbf79-0ab1-4064-b828-6bbbb56cbec2
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 18: Test Your New Message Enrichment Solution
In this step, you test your solution by using the WSClient application to send a message to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and seeing if the MLLPReceive application receives an HL7-formatted message as expected.  
  
### To test your solution  
  
1.  Open a command prompt.  
  
    > [!NOTE]
    >  Step 2 requires that you have installed the MLLP Test tool using the custom installation procedure. If the \MLLP Utilities directory containing MllpReceive.exe and MllpSend.exe does not exist on your computer, install them by performing a custom installation. For information, see [Performing a Custom Installation](../Topic/Performing%20a%20Custom%20Installation1.md).  
  
2.  At the command prompt, type **cd \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\MLLP Utilities** (where \<*drive*> is your installation drive letter), and then press **Enter**.  
  
3.  At the command prompt, type **mllpreceive /p 11000 /eb 11 /sb 28 /cr 13**, and then press **Enter**. This runs the MLLP listener application listening to port 11000 and specifying the default EB, SB, and CR characters of the MLLP message, and displays any messages received to the screen.  
  
4.  Open a second command prompt.  
  
5.  At the command prompt, type **cd \<*drive*>:\Tutorial\WSClient\bin\Debug**, and then press **Enter**.  
  
6.  At the command prompt, type **wsclient john henry smith 123456789**, and then press **Enter**. This sends a message to the Web service that contains a sample message with a patient name of John Henry Smith and a sample social security number of 123456789.  
  
7.  After a short pause, the MLLPReceive application displays the incoming MLLP message. The message should look similar to the following:  
  
    ```  
    MSH|^~\&|TestTrailing^Delimiters|srcFac^srcFacUid|dstApp^dstAppUid|dstFac^dstFacUid|200307092343|sec|ADT^A04|msgid2134|P|2.2PID|||123456789||smith^john  
    ```  
  
     If you do not receive a response after a few minutes, you should check the Application event log for any errors and begin troubleshooting.  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)