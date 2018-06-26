---
title: "Pipeline Templates | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipelines, templates"
  - "Pipeline Designer, templates"
  - "send pipelines, templates"
  - "receive pipelines, templates"
ms.assetid: b9779159-e49d-47fb-aa1c-06be5d604c67
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Pipeline Templates
In addition to the default pipelines, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes two pipeline templates: a receive pipeline template and a send pipeline template. From a BizTalk project in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], you can add a pipeline template to your project by using the **Add New Item** command on the **Project** menu. Each template has an associated policy file, which determines the pipeline's stages and indicates which pipeline components are allowed in the pipeline. While you cannot reorder the stages in a policy file, you can use Pipeline Designer to reorder the components within a stage.  
  
 A policy file specifies:  
  
- The sequence of stages.  
  
- The number of components allowed per stage.  
  
- The execution mode of each stage.  
  
  The policy files for the pipeline templates are stored in *\<BizTalk Server installation directory\>*\Developer Tools\Pipeline Policy Files. Do not modify the policy files. To make changes to a pipeline, open the pipeline template and use Pipeline Designer to modify it. For more information about using Pipeline Designer, see [Using Pipeline Designer](../core/using-pipeline-designer.md).  
  
  The empty pipeline template files are stored in *\<BizTalk Server installation directory\>*\Developer Tools\BizTalkProjectItems, and are named BTSReceivePipeline.btp and BTSTransmitPipeline.btp. The file name extension .btp indicates that the file is a BizTalk Server pipeline and can be edited in Pipeline Designer.  
  
## See Also  
 [Types of Pipelines](../core/types-of-pipelines.md)   
 [Types of Pipeline Components](../core/types-of-pipeline-components.md)   
 [Default Pipelines](../core/default-pipelines.md)   
 [Pipeline Components](../core/pipeline-components.md)   
 [About Pipelines, Stages, and Components](../core/about-pipelines-stages-and-components.md)