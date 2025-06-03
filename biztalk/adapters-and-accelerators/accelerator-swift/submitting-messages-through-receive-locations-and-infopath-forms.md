---
description: "Learn more about: Submitting Messages Through Receive Locations and InfoPath Forms"
title: "Submitting Messages Through Receive Locations and InfoPath Forms"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Submitting Messages Through Receive Locations and InfoPath Forms
Receive locations receive messages for submission into [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] applications. You can define receive locations as physical endpoints configured to receive messages using a specified transport protocol. For example, a receive location may be configured to receive files dropped to a particular file system folder using the FILE transport.  
  
 You create receive locations for receive ports that logically group and manage receive locations. For each receive location you specify a receive pipeline, which does the actual processing (decoding, disassembly, validation, and so on) of messages received at that particular receive location. A4SWIFT binds receive locations to receive ports that logically group and manage receive locations.  
  
 To submit a SWIFT message into an A4SWIFT application through a receive location, the message must be dropped to a configured receive location, processed by a receive pipeline using the SWIFT disassembler, parsed and validated by the SWIFT disassembler, and published to the MessageBox database. After messages are published to the MessageBox database, other components in your A4SWIFT application retrieve the messages (using subscriptions) for additional processing. For example, you can use send ports for final routing.  
  
 For more information about creating and configuring receive ports and receive locations, see BizTalk Server Help.  
  
 You can also submit a new message through an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, using the Message Repair and New Submission feature. To do so, you open the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form for that message from a folder in the MRSR site. You fill in the data in the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, sign it using your certificate, and then submit it. The Message Repair and New Submission orchestration processes the message.  
  
## See Also  
 [BizTalk Accelerator for SWIFT Runtime](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)
