---
title: "Double Action PIPAutomation Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9159f7b1-cb83-41f1-8637-39c5ddcc63ae
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Double Action PIPAutomation Orchestration
The DoubleAction.odx sample illustrates how to implement an orchestration to automatically generate responses for the double-action Partner Interface Processes (PIPs) 0C2, 0C4, 3A2, and 3A4. You can extend this sample project to support additional double-action PIPs.  
  
> [!NOTE]
>  The maps provided in the sample folder are samples. To use them, you must change them based on your specific requirements.  
  
> [!NOTE]
>  You should extend this sample project to support double-action PIPs only, not single-action PIPs. This orchestration will return an error if you extend it to process a single-action PIP. To ensure that this orchestration will not process single-action PIPs, see the Filtering Out Single-Action Messages section below.  
  
 By default, the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Setup program installs this sample in \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft 2013 BizTalk Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction.  
  
 This sample project includes:  
  
- A stored procedure (`PipAutomationGetAction)` to retrieve new action messages for the PIPs 0C2, 0C4, 3A2, and 3A4.  
  
- A receive location (MessagesToLOB_Receive_Location) bound to the SQL stored procedure.  
  
- An orchestration (DoubleAction.odx) that processes each PIP, generates the appropriate response based on a map for each PIP, and saves the response in the MessagesFromLOB table of the BTARNDATA database. The orchestration uses the `RNIFSubmit` method from Microsoft.Solutions.BTARN.Shared.dll to submit the message.  
  
- A binding file (DoubleActionBinding.xml) that the file Setup.bat uses to create the MessagesToLOB_Receive_Port for use with the DoubleAction orchestration.  
  
- A setup file to build and initialize the sample. If BizTalk Server is running on a 32-bit computer, run the file setup.bat in the \<drive\>:\Program Files\Microsoft Microsoft 2013 BizTalk Accelerator for RosettaNet \SDK\PIPAutomation\DoubleAction folder. If BizTalk Server is running on a 64-bit computer, run setupx64.bat in the same folder.  
  
  The orchestration receives messages using the PipAutomationGetAction stored procedure in the BTARNData database (the source file is DoubleAction.sql in the DoubleAction directory). This stored procedure retrieves the messages from the MessagesToLOB table.  
  
  To extend this sample project to support additional double-action PIPs, add a path in the orchestration for the double-action PIP. This path will include a map that will construct a respond message to a request message. For example maps, see the [3A2 Request to 3A2 Response Map Sample](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md) and the [3A4 Request to 3A4 Response Map Sample &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md).  
  
### To build and initialize this sample  
  
1. At a command prompt, locate the *\<drive\>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for RosettaNet 2013 \SDK\PIPAutomation\DoubleAction folder.  
  
   > [!NOTE]
   >  Before running the Setup program, open the file DoubleAction.sql (in the above folder) in Notepad. On the **File** menu, click **Save As**. In the **Encoding** list, select **ANSI**, and then click **Save**. Click **Yes** to overwrite the existing file.  
  
2. If your BizTalk Server is running on a 32-bit computer, run the file setup.bat in the \<drive\>:\Program Files\Microsoft BizTalk Accelerator for RosettaNet 2013 \SDK\PIPAutomation\DoubleAction folder. If your BizTalk Server 2013 installation is running on a 64-bit computer, run setupx64.bat in the same folder. The batch file will perform the following actions:  
  
   - Creates a SQL stored procedure (`PipAutomationGetAction`) in the BTARNDATA database to retrieve the action message from the MessagesToLOB table. This also ensures that the retrieved records will not be read again.  
  
   - Compiles the HeaderHelper [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] project and registers the assembly in the global assembly cache.  
  
   - Creates and binds the BizTalk Server SQL receive port (MessagesToLOB_Receive_Port).  
  
   - Enables the receive location (MessagesToLOB_Receive_Location).  
  
   - Compiles and deploys the Double-Action PIPAutomation Orchestration (DoubleAction.odx).  
  
   - Binds and starts the BizTalk Server orchestration.  
  
     > [!NOTE]
     >  The sample displays some warnings while compiling. You can ignore these warnings.  
  
     > [!NOTE]
     >  The sample uses the default host name **BizTalkServerApplication** when deploying the project. If you would like to run the sample under a different host, you will need to edit the default host names found in DoubleActionBinding.xml under \<SDK\>\PIPAutomation\DoubleAction folder.  
  
### To run the Double-Action PIPAutomation sample  
  
1. Create a 3A4 agreement where the home role is an initiator. Set the GBI for the home organization to 123456789, and set the GBI for the partner to 987654321. This lets you use the samples provided in the SampleInstances folder under the LOBApplication folder in the SDK.  
  
2. Using the Loopback agreement-mirroring utility, create a mirror for the 3A4 PIP created in step 1.  
  
3. Using the LOBApplication.exe SDK utility, submit a 3A4 PIP Request message. The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes an input sample in the folder \<*Installation Directory*\>\SDK\LOBApplication\SampleInstances\3A4_Request.xml.  
  
4. Run the following query on the BTARNDATA database:  
  
   ```  
   Select * from MessagesToLOB  
   ```  
  
5. After several seconds, four new messages appear in this table. Two of them are acknowledgment signals. One signal is the Async 3A4 Request Message. One signal is the Async 3A4 Response Message.  
  
   > [!NOTE]
   >  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat again.  
  
## Remarks  
 The public orchestration automatically generates acknowledgments (ACK and NACK signal messages). The line-of-business (LOB) application does not need to generate them.  
  
 The format of the message that is routed to the MessagesFromLOB table is called LOBMessage. The schema is available in C:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for RosettaNet 2013 \SDK\RNIFSchemas\GlobalSchemas\LOBMessage.xsd. If you use the `RNIFSubmit` method, you do not have to work with the message format. You only need to submit the ServiceContent with the additional information. `RNIFSubmit` populates the record in the MessagesFromLOB table.  
  
## Filtering Out Single-Action Messages  
 This orchestration should receive only double-action messages. You should not extend this sample project to support single-action PIPs. BTARN will post errors if you use this orchestration to process single-action messages. In order to prevent the orchestration from receiving a single-action message, change the following line in the PIPAutomationGetAction stored procedure:  
  
```  
SELECT PIPInstanceID,DestinationPartyName,SourcePartyName,PIPCode,PIPVersion,ServiceContent FROM MessagesToLOB  
```  
  
 To the above line, add a WHERE clause that will filter out single-action messages. Include in the WHERE clause all the single-action messages that you will be processing. The line should be as follows:  
  
```  
SELECT PIPInstanceID,DestinationPartyName,SourcePartyName,PIPCode,PIPVersion,ServiceContent FROM MessagesToLOB WHERE PIPCode NOT IN ( '0A1', '3B2', '3C3', '0C1', '0C3' )  
```  
  
## See Also  
 [3A2 Request to 3A2 Response Map Sample](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)   
 [3A4 Request to 3A4 Response Map Sample](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md)   
 [Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)