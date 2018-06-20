---
title: "Step 8: View Messages in the BTARN Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, viewing"
  - "loopback tutorial, viewing messages"
  - "databases, viewing messages"
ms.assetid: c549670c-4428-483c-906c-eff163ddef9a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 8: View Messages in the BTARN Databases
In this step, you use SQL Query Analyzer to view line-of-business (LOB) messages stored in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] database to verify that your loop-back scenario is working correctly.  
  
 After the LOB Application utility generates an LOB message and submits it to [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the following events occur for the initiator (home) and the responder (partner):  
  
 Initiator Workflow  
  
- SubmitRNIF submits the LOB message to the MessagesFromLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] DATA database.  
  
- The SQL adapter receive location picks up the message and delivers it to the MessageBox database. The SQL adapter picks up one message at a time running the `GetMessagesFromLOB` stored procedure.  
  
- The private initiator picks the message from the MessageBox database and then drops it again to the MessageBox database with additional promoted context properties.  
  
- The public initiator picks the message from the MessageBox database based on the subscription filter.  
  
- The HTTP send port picks the message with the RNIFSend pipeline based on the subscriptions. It saves the message in the MessageStorageOut table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Archive database for non-repudiation, and then sends the message over to the RNIFSend.aspx page.  
  
- The RNIFSend.aspx page receives the MIME-encoded message with query string variables that include the final destination of the message (partner organization URL).  
  
  Responder Workflow  
  
- [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] sends the RNIF message to the RNIFReceive.aspx page where the MIME-decoded wrapper is removed. The message is identified as either synchronous or asynchronous, and then forwarded to either the synchronous or asynchronous receive location (RNIF_Sync_Receive or RNIF_Async_Receive).  
  
- The HTTP receive location first saves the wire format of the message in the MessageStorageIn table for non-repudiation of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Archive database. The HTTP receive location then decodes, decrypts (for RNIF 2.0), validates on its signature, disassembles the XML message parts, authorizes based on the signature, and then drops it in the MessageBox database with the correct promoted properties  
  
- The public responder picks the message parts based on subscription, and then validates and processes the message based on the correct RNIF standard. The service content part drops the message into the MessageBox database with the correct context properties.  
  
- The SQL send port picks the message based on the subscription filter. It then saves the message in the MessagesToLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] DATA database.  
  
> [!NOTE]
>  On the responder side, the Public Responder is responsible for generating the acknowledgement receipt or the exception signal back to the initiator. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not save the signal message in the MessagesFromLOB table. This is because the LOB application does not generate the signal message. The Action message will continue through the Private Responder, and [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] saves it to the MessagesToLOB table.  
> 
> [!NOTE]
>  For double-action PIPs, the LOB on the responder side is responsible for generating a response message. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] drops it to the MessagesFromLOB table to go through the same process as the initiator-side process. In this case, the Public Initiator Process on the initiator side sends back an acknowledgement receipt or exception signal for the response message.  
  
### To view messages in the BTARN databases  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft SQL Server \<version\>**, and then click **SQL Server Management Studio**.  
  
2. In the Connect to Server dialog box, click **Connect**.  
  
   > [!NOTE]
   >  In the Object Explorer pane, verify that the SQL Server Agent is started. If not, right-click **SQL Server Agent**, and click **Start**.  
  
3. In the Microsoft SQL Server Management Studio, click **New Query**.  
  
4. In the Blank Query window, type the following:  
  
   ```  
   use BTARNArchive  
   SELECT * FROM         MessageStorageIn ORDER BY TIMECREATED ASC  
   SELECT * FROM         MessageStorageOut ORDER BY TIMECREATED ASC  
  
   use BTARNData  
   SELECT     * FROM         MessagesFromLOB ORDER BY TIMECREATED ASC  
   SELECT     * FROM         MessagesToLOB ORDER BY TIMECREATED ASC  
   SELECT     * FROM         Attachments ORDER BY TIMECREATED ASC  
   ```  
  
5. In the Microsoft SQL Server Management Studio, click **Execute**.  
  
   You will see an action message in the MessagesFromLOB table, and if you run the query again in several minutes (time may vary depending on your system configuration), you will see two messages generated in the MessagesToLOB table with MessageCategory values of AsyncAckSignal (25) and AsyncAction (10).  
  
## See Also  
 [Loopback](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md)   
 [Loopback Tutorial](../../adapters-and-accelerators/accelerator-rosettanet/loopback-tutorial.md)
