---
title: "IPipelineContext Members (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6a57420-85e9-43fe-8fd2-4a2aabe54c0a
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IPipelineContext Members (COM)
[IPipelineContext Interface (COM)](../core/ipipelinecontext-interface-com.md)  
  
## Public Properties  
  
|||  
|-|-|  
|![](../core/media/pubproperty.gif "pubproperty") [ComponentIndex](../core/ipipelinecontext-componentindex-property-com.md)|Gets the index of the current component in the stage.|  
|![](../core/media/pubproperty.gif "pubproperty") [PipelineID](../core/ipipelinecontext-pipelineid-property-com.md)|Gets the ID of the pipeline to which this component belongs.|  
|![](../core/media/pubproperty.gif "pubproperty") [PipelineName](../core/ipipelinecontext-pipelinename-property-com.md)|Gets the name of the pipeline.|  
|![](../core/media/pubproperty.gif "pubproperty") **ResourceTracker**|Reports the objects used during execution.|  
|![](../core/media/pubproperty.gif "pubproperty") [StageID](../core/ipipelinecontext-stageid-property-com.md)|Gets the ID of the stage in the pipeline.|  
|![](../core/media/pubproperty.gif "pubproperty") [StageIndex](../core/ipipelinecontext-stageindex-property-com.md)|Gets the index of the pipeline stage where the current component is located.|  
  
## Public Methods  
  
|||  
|-|-|  
|![](../core/media/pubmethod.gif "pubmethod") [GetDocumentSpecByName](../core/ipipelinecontext-getdocumentspecbyname-method-com.md)|Gets an [IDocumentSpec](../core/idocumentspec-interface-com.md) object for the specified document name.|  
|![](../core/media/pubmethod.gif "pubmethod") [GetDocumentSpecByType](../core/ipipelinecontext-getdocumentspecbytype-method-com.md)|Gets an [IDocumentSpec](../core/idocumentspec-interface-com.md) object for the specified document type.|  
|![](../core/media/pubmethod.gif "pubmethod") [GetGroupSigningCertificate](../core/ipipelinecontext-getgroupsigningcertificate-method-com.md)|Gets the signing certificate for the group.|  
|![](../core/media/pubmethod.gif "pubmethod") [GetMessageFactory](../core/ipipelinecontext-getmessagefactory-method-com.md)|Get access to the helper interface to work with BizTalk Server message objects.|  
  
## See Also  
 [IPipelineContext Interface (COM)](../core/ipipelinecontext-interface-com.md)