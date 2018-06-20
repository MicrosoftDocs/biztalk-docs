---
title: "ACK Message Schema Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemas, ACK schemas"
  - "acknowledgements, ACK schema types"
  - "ACK messages"
ms.assetid: da6981a0-a70a-481e-8db4-4a6851f205f1
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ACK Message Schema Types
Acknowledgment message schemas come in two forms:  

- **General acknowledgment (ACK)**. You can use a general acknowledgment (ACK) where the application does not define a special line-of-business application level acknowledgment message or where an error occurred that precludes application processing. You can also use it for accept level acknowledgments. The following table lists the ACK message structure.  


  | ACK^varies^ACK | General acknowledgment | Chapter |
  |----------------|------------------------|---------|
  |      MSH       |     Message Header     |    2    |
  |      MSA       | Message Acknowledgment |    2    |
  |    [ ERR ]     |         Error          |    2    |


- **Delayed acknowledgment (MCF)**. This message exists only for backward compatibility with HL7 Version 2.1. You use it as part of the protocol that creates a generic form of an asynchronous application level acknowledgment, the MCF message. The following table lists the MCF message structure.  

  |MCF^varies^ACK|Delayed Acknowledgment|Chapter|  
  |--------------------|----------------------------|-------------|  
  |MSH|Message Header|2|  
  |MSA|Message Acknowledgment|2|  
  |[ ERR ]|Error|2|  

  Acknowledgment messages have the MSH9 field set as either **ACK^\<**<em>trigger event</em>**\>^ACK** or **MCF^\<**<em>trigger event</em>**\>^ACK**. As a result, the first component of MSH9 is sufficient to determine the ACK schema. The document name that the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) pipeline uses always contains HL7 as the namespace. The type name is the contents of the MSH9_1 field, which is ACK or MCF. As a result, as in the example above, the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] pipeline looks for a schema with the names HL7.ACK or HL7.MCF, depending on the value of the MSH9_1 field. The schema for the message body is the same for all 2.X version messages.  

> [!NOTE]
>  In a batch in/batch out ACK scenario, the contents of the ACK header is as follows:  

- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sets MSH1, 2, 8 and 15 to what you configure in the user interface.  

- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sets MSH7 to the system time.  

- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sets MSH9 to ACK.  

- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sets MSH12 to 2.4 or 2.5.  

## See Also  
 [Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)   
 [Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)   
 [Acknowledgment Error Conditions](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)