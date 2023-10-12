---
description: "Learn more about: Microsoft.BizTalk.DefaultPipelines Reference"
title: "Microsoft.BizTalk.DefaultPipelines Reference"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Microsoft.BizTalk.DefaultPipelines Reference
The **Microsoft.BizTalk.DefaultPipelines** namespace contains the following pipelines:  
  
- XMLReceive  
  
- PassThruReceive  
  
- XMLTransmit  
  
- PassThruTransmit  
  
  A pipeline is a software component that defines and links one or more stages for processing messages received or sent by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The stages include functions such as encoding or decoding, disassembling or assembling, and decrypting or encrypting. These functions are implemented in a specific order. You can use Pipeline Designer to create receive and send pipelines.  
  
  The default pipeline references included in a BizTalk project can process all types of documents using the **PassThruReceive** and **PassThruTransmit** pipelines.  
  
  The following lists show the default components in the default pipelines. These lists also indicate the default order of the components in each pipeline. You can add and delete components if necessary.  
  
  The default components in the default XMLReceive pipeline are:  
  
- Decrypter  
  
- Decoder  
  
- Disassembler  
  
- Validator  
  
- Party Resolution  
  
  The default components in the default XMLTransmit pipeline are:  
  
- Assembler  
  
- Encoder  
  
- Encrypter  
  
## See Also  
 [Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md)   
 [About BizTalk Namespace References Included in BizTalk Projects](../core/about-biztalk-namespace-references-included-in-biztalk-projects.md)
