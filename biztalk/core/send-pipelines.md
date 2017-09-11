---
title: "Send Pipelines | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send pipelines, message flow"
  - "send pipelines, about send pipelines"
  - "messages, message flow"
  - "send pipelines, stages"
  - "pipelines, send pipelines"
  - "messages, send pipelines"
ms.assetid: c963b2d8-3b2b-4575-8105-c750deae8189
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Send Pipelines
The following figure shows the message processing workflow, highlighting the send pipeline.  
  
 ![Diagram of workflow for processing a message.](../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")  
Depicts the message processing workflow.  
  
 A send pipeline is responsible for processing documents before sending them to their final destinations. The send pipeline takes one message and produces one message to send.  
  
 You can create a new send pipeline or you can use one of the two default send pipelines included in BizTalk Server—the pass-through send pipeline and the XML send pipeline.  
  
 By default, the send pipeline consists of three empty stages: Pre-assemble, Assemble and Encode. This topic contains design considerations for populating these stages.  
  
> [!NOTE]
>  A send pipeline can produce zero messages when a consuming component is added to the pipeline.  
  
## Pre-assemble stage  
  
-   This stage is a placeholder for custom components that should perform some action on the message before the message is serialized.  
  
-   This stage is run once per message.  
  
-   This stage can contain between zero and 255 components.  
  
-   All components in this stage are run.  
  
## Assemble stage  
  
-   Components in this stage are responsible for assembling or serializing the message and converting it to or from XML.  
  
-   This stage accepts zero components or one component.  
  
-   All components in this stage are run.  
  
## Encode stage  
  
-   This stage is used for components that encode or encrypt the message.  
  
    -   Place the MIME/SMIME Encoder component or a custom encoding component in this stage if message signing is required.  
  
-   This stage is run once per message.  
  
-   This stage can contain between zero and 255 components.  
  
-   All components in this stage are executed.  
  
## See Also  
 [Receive Pipelines](../core/receive-pipelines.md)   
 [About Pipelines, Stages, and Components](../core/about-pipelines-stages-and-components.md)   
 [Types of Pipelines](../core/types-of-pipelines.md)   
 [Default Pipelines](../core/default-pipelines.md)   
 [Pipeline Templates](../core/pipeline-templates.md)   
 [Pipeline Components](../core/pipeline-components.md)   
 [Types of Pipeline Components](../core/types-of-pipeline-components.md)