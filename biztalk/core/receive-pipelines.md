---
description: "Learn more about: Receive Pipelines"
title: "Receive Pipelines"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Receive Pipelines
The following figure shows the message processing workflow, highlighting the receive pipeline.  
  
 ![Diagram of the message processing workflow.](../core/media/ebiz-dev-busprcsb.gif "ebiz_dev_busprcsb")  
Depicts the message processing workflow.  
  
 A receive pipeline operates on a message after it is received by the receive adapter. The receive pipeline takes the initial message, performs some transformations, and disassembles the raw data into zero, one, or multiple messages. These individual messages can then be processed by BizTalk Server.  
  
> [!NOTE]
>  A receive pipeline can produce zero messages if a consuming component is added to the pipeline. In this case, the pipeline component consumes the message and does not produce any output messages. If a consuming component is placed after a disassembling component, pipeline execution stops after the first message is consumed and no subsequent messages are retrieved from the disassembling component.  
  
 When creating a business process, you can create a new receive pipeline or you can use one of the two default receive pipelines included in BizTalk Server—the pass-through receive pipeline or the XML receive pipeline. For more information about these default pipelines, see [Default Pipelines](../core/default-pipelines.md).  
  
 The receive pipeline consists of four stages: Decode, Disassemble, Validate, and ResolveParty. This topic contains design considerations for populating these stages.  
  
> [!NOTE]
>  In this release, changing the order or presence of these stages in a pipeline is not supported.  
  
## Decode stage  
  
-   This stage is used for components that decode or decrypt the message.  
  
    -   The MIME/SMIME Decoder pipeline component or a custom decoding component should be placed in this stage if the incoming messages need to be decoded from one format to another.  
  
-   This stage takes one message and produces one message.  
  
-   This stage can contain between zero and 255 components.  
  
-   All components in this stage are run.  
  
## Disassemble stage  
  
-   This stage is used for components that parse or disassemble the message.  
  
    -   The components within this stage probe the message to see if the format of the message is recognized. Based on the recognition of the format, one of the components disassembles the message.  
  
    -   If this stage contains more than one component, only the first component that recognizes the message format is run. If none of the components within the stage recognize the message format, the message processing fails.  
  
    -   This stage should include any custom components that implement special behavior to disassemble the message contents.  
  
    -   This stage can contain between zero and 255 components. If there are no components in the stage, the message is passed through.  
  
## Validate stage  
  
-   This stage is used for components that validate the message format.  
  
    -   A pipeline component processes only messages that conform to the schemas specified in that component. If a pipeline receives a message whose schema is not associated with any component in the pipeline, that message is not processed. Depending on the adapter that submits the message, the message is either suspended or an error is issued to the sender.  
  
    -   Components in this stage are used to validate the XML messages produced by the Disassemble stage. Components in this stage specify schemas to perform the XML validation.  
  
-   This stage can contain between zero and 255 components.  
  
-   All components in this stage are run.  
  
    -   This stage may be run more than once. It runs once per message created by the Disassemble stage.  
  
## ResolveParty stage  
  
-   This stage is a placeholder for the [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).  
  
-   This stage may be run more than once. It runs once per message created by the Disassemble stage.  
  
-   This stage can contain between zero and 255 components.  
  
-   All components in this stage are run.  
  
## See Also  
 [Send Pipelines](../core/send-pipelines.md)   
 [About Pipelines, Stages, and Components](../core/about-pipelines-stages-and-components.md)   
 [Types of Pipeline Components](../core/types-of-pipeline-components.md)   
 [Default Pipelines](../core/default-pipelines.md)   
 [Pipeline Templates](../core/pipeline-templates.md)   
 [Pipeline Components](../core/pipeline-components.md)   
 [Types of Pipelines](../core/types-of-pipelines.md)
