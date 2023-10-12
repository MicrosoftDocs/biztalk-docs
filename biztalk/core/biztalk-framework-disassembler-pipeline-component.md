---
description: "Learn more about: BizTalk Framework Disassembler Pipeline Component"
title: "BizTalk Framework Disassembler Pipeline Component"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# BizTalk Framework Disassembler Pipeline Component
The BizTalk Framework Disassembler pipeline component parses XML data and determines whether it contains a BizTalk Framework-based messaging payload. The pipeline component saves the message context, and a new message context is created with the BizTalk Framework property that needs to be generated. This property is used to route the message to the BizTalk Framework inbound handler, so it can receive the message to process.  
  
 The BizTalk Framework Disassembler pipeline component generates an acknowledgment for the generated message if the sender requested one using the deliverReceiptRequest header within the BizTalk Framework envelope. This is controlled by the generate delivery receipt property in the BizTalk Framework Assembler pipeline component. For more information about the BizTalk Framework, see [BizTalk Framework Assembler Pipeline Component](../core/biztalk-framework-assembler-pipeline-component.md).  
  
 For information about configuring the BizTalk Framework Disassembler pipeline component and creating the orchestration, see [How to Configure the BizTalk Framework Disassembler Pipeline Component](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md).  
  
## See Also  
 [How to Configure the BizTalk Framework Disassembler Pipeline Component](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md)   
 [Pipeline Components](../core/pipeline-components.md)
