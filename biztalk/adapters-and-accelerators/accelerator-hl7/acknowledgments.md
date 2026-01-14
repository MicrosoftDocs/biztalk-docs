---
description: "Learn more about: Acknowledgments"
title: "Acknowledgments"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: concept-article
---
# Acknowledgments
You configure HL7 acknowledgments at the party level using Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) Configuration Explorer. Acknowledgments apply to parties that are sending HL7 messages through a receive location (possibly the MLLP adapter) and the HL7 2.X receive pipeline. When a message completes parsing and validation, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] can create an acknowledgment message that contains the result (success or error) of the validation process. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] can return acknowledgment messages in one of two ways. If the original sending party submitted the original message through a two-way receive port configuration, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] returns the acknowledgment message through that original port location. If the original sending port submitted the original message through a one-way receive port, then [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] submits the acknowledgment message into the MessageBox database and routes it using the subscription model.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] performs party association for receive message processing automatically based on the value within the sending application field of the HL7 message (MSH 3.1).  
  
## See Also  
 [Message Flow](../../adapters-and-accelerators/accelerator-hl7/message-flow.md)
