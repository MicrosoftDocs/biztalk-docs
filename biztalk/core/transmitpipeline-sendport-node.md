---
description: "Learn more about: TransmitPipeline (SendPort Node)"
title: "TransmitPipeline (SendPort Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TransmitPipeline node [binding file]"
ms.assetid: cee55451-6c3f-4e37-aef9-870d4b5d23aa
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# TransmitPipeline (SendPort Node)
The TransmitPipeline node of the SendPort node of a binding file provides specific information about the send pipeline bound to a send port exported with a binding file.  
  
## Nodes in the TransmitPipeline node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the send pipeline.|Not required|Default value: empty|  
|FullyQualifiedName|Attribute|xs:string|Specifies the fully qualified name of the pipeline, which includes the name of the assembly that the pipeline was deployed as a part of|Not required|Default value: empty|  
|Type|Attribute|xs:int|Specifies the type of pipeline.|Required|Default value: none<br /><br /> Possible values are documented in the [Microsoft.BizTalk.ExplorerOM.PipelineType](https://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetype.aspx) enumeration.|  
|TrackingOption|Attribute|PipelineTrackingTypes (SimpleType)|Specifies the tracking options for the pipeline.|Required|Default value: none<br /><br /> Possible values are documented in the [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](https://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetrackingtypes.aspx) enumeration.|  
|Description|Attribute|xs:string|Specifies a description for the send pipeline.|Not required|Default value: empty|
