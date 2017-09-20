---
title: "BAM Activities Created to Track EDI-AS2 Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a10ab846-0fbb-46f5-920e-cb2b5be75814
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM Activities Created to Track EDI-AS2 Messages
[!INCLUDE[prague](../includes/prague-md.md)] includes BAM activities that have been created for EDI and AS2 status reporting. These activities determine the data that is displayed in the status reports. This topic describes the BAM activities and the fields that are defined in them, and describes the enumeration values that are defined for certain fields in the BAM activities.  
  
 You can create a custom status report by creating a custom BAM activity. The custom activity can be based upon one of the standard activities. You can also display the contents of the message from the custom status report by querying the EdiMessageContent table in the BizTalkDTADb database. For more information, see the "Querying the EdiMessageContent Table" section below.  
  
> [!CAUTION]
>  Modifying a BAM activity may affect processing of the BizTalk EDI and AS2 runtimes, which depend upon the activities.  
  
## BAM Activities Used in Status Reporting  
 The BAM activities created to track EDI/AS2 messages are included as views in the BAMPrimaryImport database. The following table lists the BAM activities and the columns within them:  
  
|BAM Activity|Fields|  
|------------------|------------|  
|AS2InterchangeActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> Direction<br /><br /> MessageID<br /><br /> AS2From<br /><br /> AS2To<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> LastModified|  
|AS2MdnActivity|RecordID<br /><br /> ActivityID<br /><br /> AS2PartyRole<br /><br /> AS2From<br /><br /> AS2To<br /><br /> MessageID<br /><br /> MdnDateTime<br /><br /> MdnDispositionType<br /><br /> DispositionModifierExtType<br /><br /> DispositionModifierExtDescription<br /><br /> MdnEncryptionType<br /><br /> MdnSignatureType<br /><br /> MdnPayloadContentKey<br /><br /> MdnWireContentKey<br /><br /> MdnMicValue<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> LastModified|  
|AS2MessageActivity|RecordID<br /><br /> ActivityID<br /><br /> ReceiverPartyName<br /><br /> SenderPartyName<br /><br /> AS2PartyRole<br /><br /> AS2From<br /><br /> AS2To<br /><br /> MessageID<br /><br /> MessageDateTime<br /><br /> BTSInterchangeID<br /><br /> BTSMessageID<br /><br /> MdnProcessingStatus<br /><br /> MessageEncryptionType<br /><br /> IsMdnExpected<br /><br /> MicAlgorithmType<br /><br /> MessageSignatureType<br /><br /> MessagePayloadContentKey<br /><br /> MessageWireContentKey<br /><br /> MessageMicValue<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> IsAS2MessageDuplicate<br /><br /> DaysToCheckDuplicate<br /><br /> FileName<br /><br /> TrackingActivityID<br /><br /> LastModified|  
|BatchingActivity|RecordID<br /><br /> ActivityID<br /><br /> BatchStatus<br /><br /> DestinationPartyID<br /><br /> DestinationPartyName<br /><br /> ActivationTime<br /><br /> BatchOccurrenceCount<br /><br /> EdiEncodingType<br /><br /> BatchType<br /><br /> TargetedBatchCount<br /><br /> ScheduledReleaseTime<br /><br /> BatchElementCount<br /><br /> RejectedBatchElementCount<br /><br /> BatchSize<br /><br /> LastBatchAction<br /><br /> CreationTime<br /><br /> ReleaseTime<br /><br /> BatchReleaseType<br /><br /> BatchServiceID<br /><br /> ActivationMessageID<br /><br /> ReleaseMessageID<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> BatchCorrelationID<br /><br /> BatchName<br /><br /> BatchID<br /><br /> LastModified|  
|BatchInterchangeActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverPartyName<br /><br /> SenderPartyName<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> Direction<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> BatchCorrelationID<br /><br /> LastModified|  
|BusinessMessageJournal|RecordID<br /><br /> ActivityID<br /><br /> MessageTrackingID<br /><br /> ActionType<br /><br /> ContainerActivityID<br /><br /> ContainerType<br /><br /> BTSInterchangeID<br /><br /> BTSMessageId<br /><br /> BTSServiceInstanceId<br /><br /> BTSHostName<br /><br /> RoutedToPartyName<br /><br /> LinkedMessageTrackingID<br /><br /> TimeCreated<br /><br /> LastModified|  
|FunctionalAckActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeActivityID<br /><br /> GroupControlNo<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> Direction<br /><br /> AckProcessingStatus<br /><br /> AckStatusCode<br /><br /> DeliveredTSCount<br /><br /> AcceptedTSCount<br /><br /> AckIcn<br /><br /> AckIcnDate<br /><br /> AckIcnTime<br /><br /> ErrorCode1<br /><br /> ErrorCode2<br /><br /> ErrorCode3<br /><br /> ErrorCode4<br /><br /> ErrorCode5<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> LastModified|  
|FunctionalGroupInfo|RecordID<br /><br /> ActivityID<br /><br /> InterchangeActivityID<br /><br /> GroupControlNo<br /><br /> FunctionalIDCode<br /><br /> TSCount<br /><br /> LastModified|  
|InterchangeAckActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> Direction<br /><br /> AckProcessingStatus<br /><br /> AckStatusCode<br /><br /> AckIcn<br /><br /> AckIcnDate<br /><br /> AckIcnTime<br /><br /> AckNoteCode1<br /><br /> AckNoteCode2<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> AckCorrelationId<br /><br /> LastModified|  
|InterchangeStatusActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> ReceiverPartyName<br /><br /> SenderPartyName<br /><br /> InterchangeDateTime<br /><br /> Direction<br /><br /> AckStatusCode<br /><br /> GroupCount<br /><br /> EdiMessageType<br /><br /> PortID<br /><br /> IsInterchangeAckExpected<br /><br /> IsFunctionalAckExpected<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> AckCorrelationId<br /><br /> TsCorrelationId<br /><br /> LastModified|  
|ResendJournalActivity|RecordID<br /><br /> ActivityID<br /><br /> TrackingActivityId<br /><br /> ResendIndex<br /><br /> ResendStatus<br /><br /> BTSInterchangeID<br /><br /> LastModified|  
|ResendTrackingActivity|RecordID<br /><br /> ActivityID<br /><br /> CorrelationId<br /><br /> AdapterPrefix<br /><br /> ResendCount<br /><br /> MaxResendCount<br /><br /> ResendInterval<br /><br /> MaxRetryCount<br /><br /> RetryInterval<br /><br /> MessageContentID<br /><br /> ResendTimeout<br /><br /> RetryTimeout<br /><br /> BTSInterchangeID<br /><br /> LastModified|  
|TransactionSetActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> Direction<br /><br /> ReceiverPartyName<br /><br /> SenderPartyName<br /><br /> ApplicationSender<br /><br /> ApplicationReceiver<br /><br /> GroupDateTime<br /><br /> GroupControlNo<br /><br /> TransactionSetId<br /><br /> DocType<br /><br /> TransactionSetControlNo<br /><br /> AckStatusCode<br /><br /> BatchProcessing<br /><br /> ProcessingDateTime<br /><br /> GroupOrdinal<br /><br /> TransactionSetOrdinal<br /><br /> MessageContentKey<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> TsCorrelationId<br /><br /> LastModified|  
  
## Data Enumerations in the BAMPrimaryImport Database  
 Some EDI and AS2 data is saved as enumerations in the tables of the BAMPrimaryImport database. When displayed in the status report, the data is shown as text. These values are as follows:  
  
|Field|Enum Values|  
|-----------|-----------------|  
|AckProcessingStatus|NotExpected = -1<br /><br /> Expected = 0<br /><br /> Received = 1<br /><br /> Sent = 2<br /><br /> Generated = 3|  
|AS2PartyRole|All = 0<br /><br /> Receiver = 1<br /><br /> Sender = 2|  
|BatchAction|Creation = 0<br /><br /> Activation = 1<br /><br /> ElementReference = 2<br /><br /> Release = 3<br /><br /> Override = 4<br /><br /> Termination = 5<br /><br /> Sent = 6<br /><br /> ToBeReleased = 7|  
|BatchStatus|All = -1<br /><br /> Defined = 0<br /><br /> Active<br /><br /> Released<br /><br /> Completed|  
|BatchType|ScheduleBased = 0<br /><br /> MessagesCountInGroup = 1<br /><br /> MessagesCountIn<br />Interchange = 2<br /><br /> CharacterCount = 3<br /><br /> ExternalTrigger = 4|  
|Direction|All = 0<br /><br /> Receive = 1<br /><br /> Send = 2|  
|DisplayAckStatusCode|All = 100<br /><br /> Accepted = 0<br /><br /> PartiallyAccepted = 1<br /><br /> Rejected = -1<br /><br /> AckExpected = 500<br /><br /> AckNotExpected = 600|  
|DispositionModifierExt<br />Description|Not Valued = 1<br /><br /> Authentication Failed = 2<br /><br /> Decryption Failed = 3<br /><br /> Insufficient Message<br />Security = 4<br /><br /> Integrity Check Failed = 5<br /><br /> Unexpected Processing <br />Error = 6|  
|DispositionModifierExt<br />Type|Not Valued = 1<br /><br /> Error = 2<br /><br /> Warning = 3|  
|EdiMessageType|X12,<br /><br /> Edifact,<br /><br /> Unknown|  
|IsMdnExpected|MDN is not expected = 0<br /><br /> MDN is expected = 1|  
|MdnDispositionType|Processed = 1<br /><br /> Failed = 2|  
|MdnProcessingStatus|All = 0<br /><br /> Processed = 1<br /><br /> Failed = 2<br /><br /> Expected = 3<br /><br /> Not Expected = 4|  
|MessageEncryptionType|Message is not encrypted = 0<br /><br /> Message is encrypted = 1|  
|MessageSignatureType|Message is not signed = 0<br /><br /> Message is signed = 1|  
|MicAlgorithmType|Unknown type = -1<br /><br /> SHA1 = 1<br /><br /> MD5 = 2|  
  
## BusinessMessageJournal BAM Activity  
 The BusinessMessageJournal BAM activity enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to correlate a received EDI interchange containing a transaction set with an outgoing batched interchange that contains the same transaction set. For more information, see [Correlating an Incoming Transaction Set with an Outgoing Batch](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md).  
  
##  <a name="BKMK_Query"></a> Querying the EdiMessageContent Table  
 The EdiMessageContent table in the BizTalkDTADb database stores the message payload, along with message metadata. From a custom status report, you can query the EdiMessageContent table to display the message contents. This is similar to how some of the status reports in the product enable you to display message contents, for example, how the AS2 Message and Correlated MDN status report enables you to display the message wire format.  
  
 You link from a custom BAM activity to the EdiMessageContent table by using the key columns in the BAM activity that correspond to the ContentKey column in the EdiMessageContent table. For example, to link from the AS2MessageActivity BAM activity to the EdiMessageContent tablme, you would use either the MessagePayloadContentKey column or the MessageWireContentKey column to link to the ContentKey column.  
  
|Table|Columns|  
|-----------|-------------|  
|EdiMessageContent<br /><br /> (in the BizTalkDTADb database)|ContentKey<br /><br /> MessageFormat<br /><br /> ContentType<br /><br /> Charset<br /><br /> TimeCreated<br /><br /> TimeInserted<br /><br /> IsOrphaned<br /><br /> ContentBinary|  
  
## See Also  
 [How Data Is Stored for EDI and AS2 Status Reports](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)   
 [Correlating an Incoming Transaction Set with an Outgoing Batch](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md)