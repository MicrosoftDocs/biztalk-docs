---
title: "Pipeline Stages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipelines, properties"
  - "CATID_AssemblingSerializer component category"
  - "CATID_Encoder component category"
  - "pipelines, stages"
  - "CATID_DisassemblingParser component category"
  - "CATID_Validate component category"
  - "ComponentCategory class attribute"
  - "CATID_Decoder component category"
  - "CATID_Any component category"
  - "CATID_PartyResolver component category"
  - "Execution Mode property"
ms.assetid: ac50c48c-6ed5-4322-95cc-af55df6bcd1c
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Pipeline Stages
This topic discusses the **Execution Mode** property and stage affinity.  
  
## Execution Mode property  
 During the execution of a pipeline, the pipeline stages can run only the first component that recognizes the message format, or all components. The property that determines the execution pattern is **Execution Mode**.  
  
> [!NOTE]
>  This property is read-only on the stages included in the pipeline templates, but understanding how it works is an important concept.  
  
 When the **Execution Mode** property is set to **All**, all the components within the stage are run in the configured sequence. This mode runs several components to complete a logical task. In this case, a run-time error results if any component encounters an error while processing a message during this pipeline stage.  
  
 When a pipeline is used to receive messages in several formats, then the **Execution Mode** property is set to **FirstMatch**. In this mode, only the first component that recognizes the message is run. If no components in the stage recognize the message, a run-time error results.  
  
 Note that each stage can have its own **Execution Mode** setting, so different stages within a pipeline can have different execution modes.  
  
> [!NOTE]
>  In this release of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], all the stages in a send pipeline and all stages except Disassemble in a receive pipeline have the value of the **Execution Mode** property set to **All**. The value of the **Execution Mode** property in the Disassemble stage is set to **FirstMatch**. You cannot change the **Execution Mode** property of a stage.  
  
#### To read pipeline stage properties  
  
1.  In Pipeline Designer, click a stage shape.  
  
2.  In the Properties window, in the **General** section, read the following properties:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Indicates the name of the stage.|  
    |**Execution Mode**|Indicates the execution pattern of the stage.<br /><br /> Valid values: **All** or **FirstMatch**|  
    |**Minimum Number of Components**|Indicates the minimum number of pipeline components that can be added to the stage.|  
    |**Maximum Number of Components**|Indicates the maximum number of pipeline components that can be added to the stage.|  
    |**StageID**|Indicates the unique identifier for the stage.|  
  
## Stage affinity  
 Pipeline components have stage affinity, meaning that they are created for use within a particular stage or stages in a pipeline.  
  
 COM-based pipeline components express their stage affinity by registering themselves using the stage ID as the implementation category, while .NET-based pipeline components specify their stage affinity by using the **ComponentCategory** class attribute. Note that it is possible for a component to associate itself with more than one stage—components can have more than one implementation category or **ComponentCategory** attribute.  
  
 The following table shows the available component categories and their associated stages.  
  
|Component category|Stage where component can be placed|Description|  
|------------------------|-----------------------------------------|-----------------|  
|CATID_Decoder {9d0e4103-4cce-4536-83fa-4a5040674ad6}|Decode|All decoding components should implement this category.|  
|CATID_DisassemblingParser {9d0e4105-4cce-4536-83fa-4a5040674ad6}|Disassemble|All disassembling and parsing components should implement this category.|  
|CATID_Validate {9d0e410d-4cce-4536-83fa-4a5040674ad6}|Validate|Validation components should implement this category.|  
|CATID_PartyResolver {9d0e410e-4cce-4536-83fa-4a5040674ad6}|ResolveParty|Stage used for Party Resolution component.|  
|CATID_Encoder {9d0e4108-4cce-4536-83fa-4a5040674ad6}|Encode|All encoding components should implement this category.|  
|CATID_AssemblingSerializer {9d0e4107-4cce-4536-83fa-4a5040674ad6}|Serialize|All serializing and assembling components should implement this category.|  
|CATID_Any {9d0e4101-4cce-4536-83fa-4a5040674ad6}|Any of these stages|If a pipeline component implements this category, it means that the component can be placed into any stage of a pipeline.|  
  
## See Also  
 [Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md)   
 [About Pipelines, Stages, and Components](../core/about-pipelines-stages-and-components.md)