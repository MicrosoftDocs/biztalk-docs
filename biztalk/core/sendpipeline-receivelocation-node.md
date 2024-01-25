---
description: "Learn more about: SendPipeline (ReceiveLocation Node)"
title: "SendPipeline (ReceiveLocation Node)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SendPipeline (ReceiveLocation Node)
The SendPipeline node of the ReceiveLocation node of a binding file provides specific information about the send pipeline bound to a receive location that is exported with the binding file.  
  
## Nodes in the SendPipeline node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the send pipeline.|Not required|Default value: empty|  
|FullyQualifiedName|Attribute|xs:string|Specifies the fully qualified name of the pipeline, which includes the name of the assembly that the pipeline was deployed as a part of|Not required|Default value: empty|  
|Type|Attribute|xs:int|Specifies the type of pipeline.|Required|Default value: none<br /><br /> Possible values are documented in the<br /><br /> [Microsoft.BizTalk.ExplorerOM.PipelineType](/dotnet/api/microsoft.biztalk.explorerom.pipeline.type) enumeration.|  
|TrackingOption|Attribute|PipelineTrackingTypes (SimpleType)|Specifies the tracking options for the pipeline.|Required|Default value: none<br /><br /> Possible values are documented in the [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](/dotnet/api/microsoft.biztalk.explorerom.pipelinetrackingtypes) enumeration.|  
|Description|Attribute|xs:string|Specifies a description for the send pipeline.|Not required|Default value: empty|
