---
title: "How to Deploy Pipelines | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IReceiveLocation interface"
  - "IReceivePort interface"
  - "deploying, pipelines"
  - "pipelines, deploying"
  - "pipelines, compiling"
  - "SendPipelineData method"
  - "pipelines, configuring"
  - "pipelines, code sample"
  - "ReceivePipelineData property"
  - "Validate method"
  - "ISendPort interface"
ms.assetid: 7a56c753-a0d4-48ed-a61d-e454bc9cd507
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Deploy Pipelines
Pipelines are compiled and deployed as part of the solution build and deploy process. The compiler calls the **Validate** method on each component, allowing the components to return compile errors on the configured information. After building, the pipeline is deployed in the same assembly with the rest of the solution when the solution is deployed.  
  
## Per-instance pipeline configuration  
 Per-instance pipeline configuration is used to modify properties of pipeline components within a deployed pipeline at the send port or receive location level. Per-instance pipeline configuration is useful when only a few pipeline component properties need to be modified per instance. For example, if you need to support different message types in multiple receive locations and have a single custom XML receive pipeline, per-instance pipeline configuration enables you to deploy the pipeline and override the default configuration (including specifying different envelope and document spec names). This mechanism is supported in the BizTalk Management console and programmatically through the Explorer object model.  
  
### Per-Instance Pipeline Configuration Using BizTalk Administration console  
 You can perform per-instance pipeline configuration using the BizTalk Management console. Once you have deployed your custom pipeline, create as many receive locations or send ports as required. Then for each receive location or send port, override default property values through the Configure Pipeline dialog box. For example, to specify a different document schema, enter a schema name for the **EnvelopeDocSpecNames** property.  
  
> [!WARNING]
>  No validation of the configuration values specified in the receive location or send port will be performed. If the configuration is incorrect, messages will fail at runtime when passing through the pipeline.  
  
### Per-Instance Pipeline Configuration Using the Explorer Object Model  
 When the XML file describing the per-instance configuration of the pipeline components is read, it overrides the properties set in the pipeline file.  
  
 Per-instance pipeline configuration is set by using the BizTalk Explorer object model. The BizTalk Explorer object model provides the **ReceivePipelineData** property on the **IReceiveLocation** and **ISendPort** interfaces for setting the configuration of receive pipeline components. The BizTalk Explorer object model also provides the **SendPipelineData** method on the **IReceivePort** and **ISendPort** interfaces for setting configuration of send pipeline components.  
  
 Per-instance pipeline configuration does not support the following:  
  
- Rearranging stages within the pipeline  
  
- Adding or removing stages  
  
- Rearranging components within stages  
  
- Adding or removing components  
  
  The only supported changes are in the configuration of pipeline components. Per-instance configuration of a pipeline component overrides the common pipeline component configuration. If a parameter of a component is not specified in per-instance pipeline configuration, the common configuration for that parameter (as configured in Pipeline Designer) is used.  
  
  The following is an example of per-instance configuration data.  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<Root xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
    <Stages>  
        <Stage CategoryId="9d0e4103-4cce-4536-83fa-4a5040674ad6">  
            <Components>  
                <Component Name=Microsoft Microsoft.BizTalk.Component.MIME_SMIME_Decoder>  
                    <Properties>  
                        <AllowNonMIMEMessage vt=11>true</AllowNonMIMEMessage>  
                    </Properties>  
                </Component>  
            </Components>  
        </Stage>  
        <Stage CategoryId="9d0e4105-4cce-4536-83fa-4a5040674ad6">  
            <Components>  
                <Component Name=Microsoft.BizTalk.Component.XmlDasmComp>  
                    <Properties>  
                        <EnvelopeSpecNames vt=8>MySchemas.EnvelopeSpecNames</EnvelopeSpecNames>  
                        <AllowUnrecognizedMessage vt=11>false</AllowUnrecognizedMessage>  
                    </Properties>  
                </Component>  
            </Components>  
        </Stage>  
        <Stage CategoryId="9d0e410d-4cce-4536-83fa-4a5040674ad6" ExecutionSequence="2">  
            <Components>  
                 <Component Name=Microsoft.BizTalk.Component.XmlValidator >  
                    <Properties>  
                        <DocumentSpecName vt=8>MySchemas.DocspecName</DocumentSpecName>  
                    </Properties>  
                </Component>  
            </Components>  
        </Stage>  
    </Stages>  
</Root>  
```  
  
## See Also  
 [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md)