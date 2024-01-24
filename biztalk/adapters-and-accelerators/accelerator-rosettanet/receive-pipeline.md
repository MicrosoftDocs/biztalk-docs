---
description: "Learn more about: Receive Pipeline"
title: "Receive Pipeline"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Receive Pipeline
This sample provides a working Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] receive pipeline that you can customize for your application.  
  
## Demonstrates  
 This sample demonstrates how to process an incoming RNIF message into the equivalent XML message using the BTARN receive pipeline (PipelineReceive.btp). PipelineReceive.btp is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines. It includes the following stages:  
  
- ReceiveMessageNonRepudiate  
  
- RNMimeDecoder (MIME Preprocessor/Decoder)  
  
- RNDAsm (XML Disassembler)  
  
- RNPartyRes (Party Resolution component)  
  
- MessageUpdater  
  
  For more information about the components of this pipeline, and the message flow in this pipeline, see [BTARN Receive Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md).  
  
## See Also  
 [Pipeline Samples](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md)   
 [BTARN Receive Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)
