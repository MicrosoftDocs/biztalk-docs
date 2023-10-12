---
description: "Learn more about: Default Pipelines"
title: "Default Pipelines"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Default Pipelines
When you create a new application, the default pipelines are created and deployed by default and appear in the Microsoft.BizTalk.DefaultPipelines assembly in the \References folder for every BizTalk project. The default pipelines cannot be modified in Pipeline Designer. These pipelines can be selected when configuring a send port or receive location in BizTalk Explorer. This topic describes the default pipelines and when to use them.  
  
> [!NOTE]
>  The XML receive and XML send pipelines do not support XML documents larger than 4 gigabytes.  
  
## PassThruReceive pipeline  
 The pass-through receive pipeline has no components. It is used for simple pass-through scenarios when no message payload processing is necessary. This pipeline is generally used when the source and the destination of the message are known, and the message requires no validation, encoding, or disassembling. This pipeline is commonly used in conjunction with the pass-through send pipeline.  
  
 Because it does not contain a disassembler, the pass-through receive pipeline cannot be used to route messages to orchestrations.  
  
> [!NOTE]
>  The pass-through receive pipeline does not support property promotion.  
  
## PassThruTransmit pipeline  
 The pass-through-send pipeline has no components. This pipeline is generally used when no document processing is necessary before sending the message to a destination.  
  
## XMLReceive pipeline  
 The XML receive pipeline consists of the following stages:  
  
-   **Decode.** Empty  
  
-   **Disassemble.** Contains the XML Disassembler component  
  
-   **Validate.** Empty  
  
-   **ResolveParty.** Runs the Party Resolution component, which resolves the certificate subject or the source security ID to the party ID.  
  
## XMLTransmit pipeline  
 The XML send pipeline consists of the following stages:  
  
-   **Pre-assemble.** Empty  
  
-   **Assemble.** Contains the XML Assembler component  
  
-   **Encode.** Empty  
  
## See Also  
 [Types of Pipelines](../core/types-of-pipelines.md)   
 [Types of Pipeline Components](../core/types-of-pipeline-components.md)   
 [Pipeline Templates](../core/pipeline-templates.md)   
 [Pipeline Components](../core/pipeline-components.md)   
 [About Pipelines, Stages, and Components](../core/about-pipelines-stages-and-components.md)
