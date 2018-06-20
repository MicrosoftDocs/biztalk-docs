---
title: "Enhanced Tracking | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tracking"
ms.assetid: 8adf78f0-ab0f-44d4-aa5b-9546e2bdf01f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Enhanced Tracking
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] provides an enhanced ability to track processes and messages. The native functionality for Business Activity Monitoring (BAM) in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is to track metadata only. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] tracks message content—both service content and headers.  

 The following table shows the full range of data tracking in [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]. This topic addresses process and message tracking. For more information about non-repudiation data, see [RNIF Message Processing](../../adapters-and-accelerators/accelerator-rosettanet/rnif-message-processing.md).  


|           Tracked information           |                                                        Feature                                                        |                                                                                   User access                                                                                   |
|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| RosettaNet process and message tracking | Through BAM (with database tables and views of the data) for metadata and proprietary interfaces for the message body |                                                                   BAM user interface or custom user interface                                                                   |
|            Errors and events            |                Through the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] event log                |                                                                                    Event log                                                                                    |
|          Non-repudiation data           |                         Through proprietary interfaces (wire formats of messages are stored)                          | MessageStorageIn and MessageStorageOut tables in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive database, and through the SDK |

## Process and Message Tracking  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] tracks two basic activities: the process activity and the message activity. The process activity tracks message processing in public-process orchestrations. The message activity tracks message processing in send or receive pipelines.  

 The process activity tracks full message metadata. The message activity tracks process activity metadata and the contents of the message.  

### Process Activity  
 Whenever a public-process orchestration (initiator or responder) is instantiated, the public process creates a process-activity record in the BAM tracking database. At various points in the public process, the orchestration saves tracking metadata. The process activity stops when the orchestration stops.  

 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] tracks complete metadata for the process in two instances:  

- When [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] is a responder and it receives a request action message  

- When [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] is an initiator and receives a request message from the line-of-business (LOB) application.  

  Whenever [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] sends or receives a message, the public process updates the status of the process activity.  

### Message Activity  
 The message activity tracks messages through the send and receive pipelines. Whenever a send or receive pipeline processes a message, the pipeline creates a message activity. The pipeline creates a message-activity record in the BAM tracking database and a message record in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive database.  

 The message activity saves the content of the message, including both service content and headers. In the receive pipeline, if the MIME decoder succeeds, the activity saves the four parts of the message content as XML in text format in the ContentXml column of the MessageContent table. If the MIME decoder fails, the activity saves the message content in binary format in the ContentBinary column of the MessageContent table.  

### Use of Tracking Data in Correlation  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] tracks the information required to correlate each process to all exchanged messages for a specific PIP (positive or negative signals, and request and response signals). It also tracks the information used to correlate a 0A1 message, if [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] sends a Notification of Failure for that PIP. The combination of the PIP instance ID, initiator party name, and destination party name determine the messages related to an activity.  

### Tracking Databases  
 The process and message activities save tracking metadata in the BAMPrimaryImport [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database. In this database, tables whose names start with the prefix "bam_Process" store process-activity tracking data, and tables whose names start with the prefix "bam_Message" store message-activity tracking data. Each separate process or message activity has a single record corresponding to it in the tables. Information about the two activities, and metadata tracking, is included in metadata tables whose names start with the prefix "bam_Metadata".  

 You can consume the data in the BAMPrimaryImport tracking database using the following views. These and other views are available in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] node of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.  

|Tracking View|Data|  
|-------------------|----------|  
|bam_Process_AllInstances|State of the RosettaNet process defined by the PIP|  
|bam_Message_AllInstances|States of all messages|  
|bam_Process_CompletedInstances|State of completed processes|  

 The message activity saves the message content in the MessageContent table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive database. You can examine the content by running a query on the MessageContent table, using the unique identifier for the message. The activity stores the unique identifier in the ContentKey column of the message-activity tracking tables, using the prefix "bam_Message.  

> [!IMPORTANT]
>  The message activity shares the message content in clear text in the MessageContent table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive database. This occurs in all tracking scenarios, including those in which messages are encrypted or signed. If you are concerned about the accessibility of the message content, you can restrict access to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive database.  

 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses the BAM tracking APIs to save tracking data.  

### Status Codes  
 The bam_Process_Active and bam_Process_Completed tables in the BAMPrimaryImport database included a Status column that indicates the state of the process. The following table shows the values for each status code.  

|Status Code|Process State|  
|-----------------|-------------------|  
|-1000|ActivityNotPresentFatalError|  
|-500|UnexpectedFatalError|  
|-100|Initiated0A1|  
|-99|TerminatedOnError<br /> (Any other termination than terminated by 0A1)|  
|-85|TerminatedBy0A1|  
|-75|TimedOutOnResponseSignal|  
|-50|TimedOutOnResponse|  
|-25|TimedOutOnActionSignal|  
|0|RegisteredActivity|  
|1|ActivityToBeInitiated|  
|10|ReceivedAction or SentAction|  
|25|ReceivedActionSignal or SentActionSignal|  
|35|ReceivedActionSignal2 or SentActionSignal2<br /> (Signal 2 is meant for RNIF v11)|  
|50|ReceivedResponse or SentResponse|  
|75|ReceivedResponseSignal or SentResponseSignal|  
|85|ReceivedResponseSignal2 or SentResponseSignal2<br /> (Signal 2 is meant for RNIF v11)|  
|100|ActivityCompleted|  

### Activity Definition File  
 The activity definition file defines the fields that you track in BAM, and how you view them. For more information about this file, see [Working with the Tracking Activity Definition File](../../adapters-and-accelerators/accelerator-rosettanet/working-with-the-tracking-activity-definition-file.md).  

 For more information about BAM, see "Business Activity Monitoring (BAM)" in BizTalk Server Help.  

## See Also  
 [Working with the Tracking Activity Definition File](../../adapters-and-accelerators/accelerator-rosettanet/working-with-the-tracking-activity-definition-file.md)   
 [What BizTalk Accelerator for RosettaNet Adds to BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)