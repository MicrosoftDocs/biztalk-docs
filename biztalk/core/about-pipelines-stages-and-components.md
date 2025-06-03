---
description: "Learn more about: About Pipelines, Stages, and Components"
title: "About Pipelines, Stages, and Components"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# About Pipelines, Stages, and Components
A pipeline is a piece of software infrastructure that contains a set of .NET or COM components that process messages in a predefined sequence. A pipeline divides processing into categories of work called stages, and determines the sequence in which the stages are performed. Each stage defines logical work groups, determines which components can go in that stage, and specifies how the pipeline components in the stage are run.  
  
 Within each stage, pipeline components perform specific tasks. For example, components within stages of a receive pipeline may decode, disassemble, and then convert documents from other formats to XML. Send pipelines do essentially the opposite: convert documents from XML to other formats, assemble, and encrypt, with each pipeline component performing a portion of the entire process. Although a stage is a container of components, each stage is itself a component with metadata. Stages have no execution code, as opposed to pipeline components, which do have execution code.  
  
 The following figure shows how the pipeline design surface illustrates pipelines. This pipeline has two stages, the Assemble stage and the Encode stage. The XML Assembler pipeline component was added to the Assemble stage, but the Encode stage is still empty, because it still shows **Drop Here!** to indicate that a pipeline component can be added to the stage.  
  
 ![Stages and components in a BizTalk pipeline](../core/media/ebiz-pipe-stages02.gif "ebiz_pipe_stages02")  
Illustrates stages and components in a BizTalk pipeline.  
  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contains a set of pipeline templates, pipeline components, and default pipelines. You can create and configure pipelines by using the Pipeline Designer user interface; you implement pipelines by using the API in the **Microsoft.BizTalk.Component.Interop** namespace. You cannot modify the pipeline templates.  
  
## In This Section  
  
-   [Types of Pipelines](../core/types-of-pipelines.md)  
  
-   [Types of Pipeline Components](../core/types-of-pipeline-components.md)  
  
-   [Pipeline Stages](../core/pipeline-stages.md)  
  
-   [Default Pipelines](../core/default-pipelines.md)  
  
-   [Pipeline Templates](../core/pipeline-templates.md)  
  
-   [Pipeline Components](../core/pipeline-components.md)  
  
-   [Schema Resolution in Pipeline Components](../core/schema-resolution-in-pipeline-components.md)  
  
-   [Envelope Use in the XML Assembler and Disassembler Pipeline Components](../core/envelope-use-in-the-xml-assembler-and-disassembler-pipeline-components.md)  
  
-   [Property Demotion in Assembler Pipeline Components](../core/property-demotion-in-assembler-pipeline-components.md)  
  
-   [Property Promotion in Disassembler Pipeline Components](../core/property-promotion-in-disassembler-pipeline-components.md)  
  
-   [Distinguished Fields in Disassembler Pipeline Components](../core/distinguished-fields-in-disassembler-pipeline-components.md)
