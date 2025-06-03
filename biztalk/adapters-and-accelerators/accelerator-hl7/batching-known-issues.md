---
description: "Learn more about: Batching Known Issues"
title: "Batching Known Issues"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: troubleshooting-known-issue
---
# Batching Known Issues
This section contains useful information that may help you avoid batching errors.  
  
## Batch trailer segment (FTS and BTS) fields are accepted even if they are strings  
 HL7 specifies the fields in FTS and BTS segments differently in the various versions of HL7. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] defines all of the fields as String data type to avoid inconsistency.  
  
## Data type of an ACK to a batch message  
 In an acknowledgment (ACK) message generated in response to a batch message, if fragmentation for source party is turned off, then the MSH10 field (message control ID) will be a GUID, rather than any other data type of the MSH10 field in the batch message.  
  
## BTAHL7 Configuration Explorer and Create Batch orchestrations are not two-way synchronized  
 You may not able to view the current status of the batch control schedule even if you press F5 in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, and may have to check both [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and the Health and Activity Tracking (HAT) tool for the current status of the batch control schedule.  
  
## Two parsing errors logged when messages in Batch In/Batch Out scenario contain validation errors  
 When the first message in the Batch In/Batch Out scenario (multiple messages batched without batch headers) contains validation errors, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] logs two errors in the Event Log. The first error pertains to the first message in the batch, and the second error pertains to the remainder of the messages.  
  
## Subscription using the BTS.MessageType property for the Batch In/Batch Out scenario with fragmentation disabled is not supported  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not support subscription using the **BTS.MessageType** property for the Batch In/Batch Out scenario with fragmentation disabled as an interchange that may consist of multiple message types.  
  
## Entire batch suspended after erroneous message in the Batch In/Batch Out scenario  
 If a message with fatal parser errors (for example, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not parse MSH 9 or MSH 12 or body schema for the message failed to load) is encountered in a fragmented Batch In/Batch Out scenario, any data after the erroneous message is suspended even if the recoverable interchange support has been enabled.  
  
## Batch of Acks get routed to the source party of the first message in Batch In/Batch Out Scenario  
 In Batch In/ Batch Out scenario batch of Acks get routed based on the source party information of the first message, because this functionality assume that for all the messages in inbound batch the source and destination parties are same.  
  
## Batch of Acks does not get routed to the source party when two-way receive port is used in Batch In/ Batch Out scenario  
 In case of request-response receive port the ACK/NACK batch does not get routed to the source party for BIBO scenario.  
  
## See Also  
 [Known Issues](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)
