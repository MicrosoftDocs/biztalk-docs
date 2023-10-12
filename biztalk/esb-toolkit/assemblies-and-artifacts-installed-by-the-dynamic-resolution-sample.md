---
description: "Learn more about: Assemblies and Artifacts Installed by the Dynamic Resolution Sample"
title: "Assemblies and Artifacts Installed by the Dynamic Resolution Sample"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Assemblies and Artifacts Installed by the Dynamic Resolution Sample
The following table lists the assemblies and artifacts installed by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Dynamic Resolution sample.  
  
|Location|Category|Name and version of the component|  
|--------------|--------------|---------------------------------------|  
|BizTalk application GlobalBank.ESB|Orchestrations|(none)|  
|BizTalk application GlobalBank.ESB|Send Ports|DynamicResolutionSolicitResp|  
|||DynamicResolutionOneWay|  
|BizTalk application GlobalBank.ESB|Receive Ports|DynamicResolutionReqResp|  
|||DynamicResolution|  
|BizTalk application GlobalBank.ESB|Receive Locations|DynamicResolutionReqResp_SOAP<br /><br /> DynamicResolution_FILE|  
|BizTalk application GlobalBank.ESB|Schemas|GlobalBank.ESB.DynamicResolution.Schemas.CNPurchaseOrderResponse Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas.NAOrderResponse Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas.CNOrderDoc Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas.CNOrderResponse Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas.CNPurchaseOrderDoc Version 2.0.0.0|  
|BizTalk application GlobalBank.ESB|Pipelines|GlobalBank.ESB.DynamicResolution.Pipelines.ESBReceiveSendXMLXML Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Pipelines.ESBReceiveXML Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Pipelines.ESBPassThrough Version 2.0.0.0|  
|BizTalk application GlobalBank.ESB|Resources|GlobalBank.ESB.DynamicResolution.Pipelines Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms Version 2.0.0.0|  
|BizTalk application GlobalBank.ESB|Policies|CanadaSubmitOrderMaps.xml|  
|||GetCanadaEndPoint.xml|  
|||GetCanadaPurchaseEndPoint.xml|  
|||ResolveMap.xml|  
|||ResolveEndPoint.xml|  
|BizTalk application GlobalBank.ESB|Vocabularies|DynamicRunTimeDocSpecs.xml<br /><br /> DynamicRunTimeEndPoints.xml<br /><br /> DynamicRunTimeMapTypes.xml<br /><br /> DynamicRunTimeServiceActions.xml|  
|BizTalk application GlobalBank.ESB|Maps|GlobalBank.ESB.DynamicResolution.Transforms.SubmitPurchaseOrderResponseCN_To_SubmitOrderResponseNA Version=2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN Version=2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitPurchaseOrderRequestCN Version=2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderResponseCN_To_SubmitOrderResponseNA Version=2.0.0.0|  
|Global assembly cache|Assemblies|GlobalBank.ESB.DynamicResolution.Pipelines Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms Version 2.0.0.0|  
|%Program Files%\\BizTalk Server\Pipeline Components|Pipeline components|(none)|
