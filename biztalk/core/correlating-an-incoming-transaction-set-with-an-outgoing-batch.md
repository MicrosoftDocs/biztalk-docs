---
title: "Correlating an Incoming Transaction Set with an Outgoing Batch | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fbe40f8-7379-42be-b8a7-070ce8a7ce26
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Correlating an Incoming Transaction Set with an Outgoing Batch
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to correlate an EDI transaction set submitted to the Batching Orchestration with an outgoing batch. You do so by correlating a status reporting entry for the transaction set submitted to the Batching Orchestration (the BTSInterchangeID) to a status reporting entry for the orchestration (ActivityID). This correlation is performed using entries in the BusinessMessageJournal BAM activity. These entries are created by the Batching Orchestration when a batch element is received.  
  
> [!IMPORTANT]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will make entries in the BusinessMessageJournal activity only if EDI status reporting and Transaction Set tracking is enabled for the agreement.  
  
 The sections below describe the following:  
  
- How [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] saves tracking data  
  
- How you can create a custom pipeline component to enable correlation  
  
- How you can correlate an incoming transaction set with an outgoing batch.  
  
- How you can query the BusinessMessageJournal activity to determine the BTSInterchangeID of the batch if you know the BTSInterchangeID of the transaction set contained in the batch.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
## Changes to the Activities  
 The Batching Orchestration makes entries in the BatchingActivity, TransactionSetActivity, and BusinessMessageJournal BAM activities. As a transaction set moves through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will make the following entries in these activity tables for the transaction set and the batch that includes it:  
  
1.  When the EDI disassembler processes an incoming EDI interchange, it creates entries in the InterchangeStatusActivity and the TransactionSetActivity tables.  
  
    > [!NOTE]
    >  For more information about the BAM activities, see [BAM Activities Created to Track EDI-AS2 Messages](../core/bam-activities-created-to-track-edi-as2-messages.md).  
  
2.  When the Batching Orchestration is instantiated, the orchestration creates an entry in the BatchingActivity. The BAM subsystem creates a value for the ActivityID.  
  
3.  After the batching orchestration has picked up the transaction set, it creates an entry for the transaction set in the TransactionSetActivity table.  
  
4.  The orchestration creates an entry in the BusinessMessageJournal activity. It sets the MessageTrackingID field of this activity to the value of the ActivityID field of the entry that the orchestration created in TransactionSetActivity table. It also sets the BTSInterchangeID field to the BTS.InterchangeID context property for the transaction set and the BTSMessageID field to the BTS.MessageID context property for the transaction set.  
  
5.  The orchestration creates a second entry in the BusinessMessageJournal activity. It sets the MessageTrackingID field to the ActivityID field of the entry that the orchestration created in TransactionSetActivity table. It sets the BTSInterchangeID field to the BTS.InterchangeID context property for the batch. It does not set the BTSMessageID. It sets the ContainerActivityID to the value of the ActivityID in the BatchingActivity.  
  
## Creating a Custom Pipeline Component for Enabling Correlation  
 To set up correlation of an incoming transaction set with an outgoing batch that contains that transaction set, you need to create a custom pipeline component. This pipeline component should come after the EDI Disassembler and before the BatchMarker component of the EDIReceive pipeline. This pipeline component needs to create an entry in the BusinessMessageJournal activity. In this entry, the BTSInterchangeID field should be set to the BTS.InterchangeID context property and the BTSMessageID field should be set to the BTS.MessageID context property.  
  
## Looking Up the InterchangeID for a Transaction Set in a Batch  
 You correlate a received interchange, and the batch that contains the transaction set from the interchange, by using the entries in the BatchingActivity table and the BusinessMessageJournal activity, as described below.  
  
### To correlate an incoming transaction set with an outgoing batch that contains that transaction set  
  
1.  Determine the value of ActivityID for the batch in the BatchingActivity table.  
  
2.  Search for the ActivityID value in the ContainerActivityID field of the BusinessMessageJournal activity table.  
  
3.  In the record identified by the ContainerActivityID, look up the value of the MessageTrackingID field, which is associated with the batch.  
  
4.  Using the value of the MessageTrackingID field associated with the batch in the BusinessMessageJournal activity table, search for the same value in the MessageTrackingID field of other records in the BusinessMessageJournal activity table. Any records found are associated with transaction sets in the batch, as recorded by the Batching Orchestration.  
  
5.  In a record associated with a transaction set in the BusinessMessageJournal activity table, look up the value of the BTSInterchangeID field.  
  
6.  Using the value of the BTSInterchangeID, you can look up a record for the transaction set that was created in the BusinessMessageJournal activity table, as recorded by the custom pipeline component. You can also look up a record for the transaction set in the TransactionSetActivity table.  
  
## Querying BusinessMessageJournal  
 If transaction set reporting is enabled, and you know the BTSInterchangeID of the received interchange, you can use the following SQL Query to find out the BTSInterchangeID of the batch that contains the transaction set submitted to the Batching Orchestration. With this code, you can create a custom application to gain visibility into the messages in a batch.  
  
> [!IMPORTANT]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will make entries in the BusinessMessageJournal activity only if EDI status reporting and Transaction Set tracking is enabled for the agreement.  
  
```  
Select MessageTrackingID  
From BusinessMessageJournal  
Where BTSInterchangeID = <given InterchangeID of the receive interchange>  
  
Select BTSInterchangeID  
From BusinessMessageJournal  
Where MessageTrackingID = <MessageTrackingID from the previous query> and BTSInterchangeID = <given InterchangeID>  
```  
  
## See Also  
 [BAM Activities Created to Track EDI-AS2 Messages](../core/bam-activities-created-to-track-edi-as2-messages.md)   
 [Enabling EDI and AS2 Status Reports](../core/enabling-edi-and-as2-status-reports.md)