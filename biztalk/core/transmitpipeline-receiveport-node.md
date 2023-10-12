---
description: "Learn more about: TransmitPipeline (ReceivePort Node)"
title: "TransmitPipeline (ReceivePort Node)"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# TransmitPipeline (ReceivePort Node)
The TransmitPipeline node of the ReceivePort node of a binding file provides specific information about the send pipeline bound to a two way receive port exported with the binding file.  
  
> [!NOTE]
>  Since send pipelines for two-way receives are bound at the receive location level in BizTalk Server, this node is provided for backwards compatibility with BizTalk Server 2004. Send pipelines for two-way receives are bound at the receive port level in BizTalk Server 2004. Properties that are set for this node of a binding file that was exported from BizTalk Server 2004 will be applied to the SendPipeline node of each two-way receive location referenced by the receive port when importing the binding file into BizTalk Server.  
  
## Nodes in the TransmitPipeline node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the send pipeline.|Not required|Default value: empty|  
|FullyQualifiedName|Attribute|xs:string|Specifies the fully qualified name of the pipeline, which includes the name of the assembly that the pipeline was deployed as a part of.|Not required|Default value: empty|  
|Type|Attribute|xs:int|Specifies the type of pipeline.|Required|Default value: none<br /><br /> Possible values are documented in the<br /><br /> [Microsoft.BizTalk.ExplorerOM.PipelineType](/dotnet/api/microsoft.biztalk.explorerom.pipelinetype) enumeration.|  
|TrackingOption|Attribute|PipelineTrackingTypes (SimpleType)|Specifies the tracking options for the pipeline.|Required|Default value: none<br /><br /> Possible values are documented in the [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](/dotnet/api/microsoft.biztalk.explorerom.pipelinetrackingtypes) enumeration.|  
|Description|Attribute|xs:string|Specifies a description for the send pipeline.|Not required|Default value: empty|  
  
## See Also  
 [SendPipeline](../core/sendpipeline-receivelocation-node.md)   
 [ReceiveLocation](../core/receivelocation-receivelocations-node.md)
