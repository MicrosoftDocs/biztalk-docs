---
description: "Learn more about: Processing a Received Acknowledgment"
title: "Processing a Received Acknowledgment"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Processing a Received Acknowledgment
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will expect a technical acknowledgment if the relevant property is specified in the agreement. For X12, this is the **TA1 Expected** property in the **Acknowledgements** page of the one-way agreement in the **Agreement Properties** dialog box or from fallback agreement properties. For EDIFACT, this is the **Receipt of message (CONTRL) expected** property in the **Acknowledgements** page of the one-way agreement in the **Agreement Properties** dialog box or from fallback agreement properties. When the receiving agreement processes the received message, it will generate the technical acknowledgment as a result of the value of ISA14 or UNB9 in the message.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will expect a functional acknowledgment for either X12 or EDIFACT encoding if the relevant property is specified in the agreement. For X12, this property is the **997 Expected** in the **Acknowledgements** page of the one-way agreement in the **Agreement Properties** dialog box or from fallback agreement properties. For EDIFACT, this property is the **Acknowledgement (CONTRL) expected** property in the **Acknowledgements** page of the one-way agreement in the **Agreement Properties** dialog box or from fallback agreement properties. When the receiving agreement processes the received message, it will generate the technical acknowledgment as a result of the value of ISA14 or UNB9 in the message.  
  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an acknowledgment to an EDI message, it validates the acknowledgment using the acknowledgment control schemas. These schemas are X12_\<version number\>*997.xsd or X12\\*\<version number\>*TA1.xsd for X12, EFACT\\*\<Version number\>_CONTRL.xsd for EDIFACT, and X12_00501_997.xsd for HIPAA 5010.  
  
 When the receive pipeline processes the incoming acknowledgment, it correlates the acknowledgment to the sent EDI interchange. The pipeline then drops the acknowledgment into the MessageBox. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not process the acknowledgment further. The acknowledgment will be suspended unless you set up a mechanism for processing it. To process the acknowledgment, you can set up a send port that subscribes to it, and then drops it into a folder where the acknowledgments can be routinely deleted.  
  
## See Also  
 [EDI Acknowledgment Structure](../core/edi-acknowledgment-structure.md)   
 [Sending an EDI Acknowledgment](../core/sending-an-edi-acknowledgment.md)
