---
title: "Schema Resolution in Pipeline Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipelines, schema resolution"
  - "pipeline components, schema resolution"
  - "schemas, pipeline components"
ms.assetid: 35a79a6f-788b-4ca1-8483-36dcba5ae580
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema Resolution in Pipeline Components
Pipeline disassembler and assembler components use XSD schemas to process messages. The schemas contain information such as the list of promoted properties, distinguished fields, annotations for flat file messages, and annotations for XML envelopes.  
  
 Standard disassembler and assembler components support retrieval of deployed schemas by using the schema type name and message type. Some components retrieve by using both the schema type name and the message type, while others (for example, the Flat File Disassembler) retrieve only by the schema type.  
  
 Pipeline components that receive XML messages determine the message type by examining the message root element and namespace. For example, the message type for the following XML is "<http://MyDocument.org#MyDocument>".  
  
```  
<ns0:MyDocument xmlns:ns0="http://MyDocument.org">  
  
</ns0:MyDocument>  
```  
  
 If a schema does not have a namespace defined for it, the message type is "\<**rootNode**\>". For example, if the preceding example XML had no namespace, the message type would be "MyDocument".  
  
 Standard pipeline components use the message type to retrieve the appropriate schema from the database. Default XML receive and send pipelines always determine which schema to load by using the message type dynamically discovered at runtime from the message XML content (unless the pipeline component is set to allow unrecognized messages). The XML Disassembler can remove the message envelope by using this mechanism; however, the XML Assembler cannot create an envelope for an outgoing message without knowing what envelope schema to use.  
  
 You specify the envelope schema in the configuration properties for the XML Assembler from within the pipeline designer.  
  
## How Schemas Are Resolved  
 Assuming you are not specifying the schema directly in the XmlDisassembler, schemas will be resolved in the following manner:  
  
1. First, an unqualified search on the deployed schemas is made using the root node name and namespace (for example, http://MyNamespace#MyRoot). If a unique match is found the schema is resolved. If multiple matches are found and differ only by version number and only one is active, that version is used and the schema is resolved. If the same schema is active in multiple applications, multiple active schemas will be found and the search will continue with step 2 below.  
  
2. If there are multiple matches that step 1 cannot resolve, the search is qualified by the assembly the pipeline is executing in. If a unique schema is found within the same assembly the pipeline is executing in, then the schema is resolved.  
  
3. If there are still no matches, then the publisher is used to resolve the schema. The search is narrowed by using the root node, namespace, and public key token. If a unique schema is found using this search, the schema is resolved.  
  
4. Schema cannot be resolved. An error is returned noting that no unique schema can be found.  
  
   For other considerations including the effect of SQL Server collation and case-sensitivity on schema resolution, see [Namespace Management](../core/namespace-management.md).  
  
   To create an envelope in the XML Assembler or a header and trailer in the Flat File Assembler, you may do one of the following:  
  
- Create a custom send pipeline and specify the schemas for the envelope in the configuration properties for the XML Assembler. This is done from within the pipeline designer.  
  
- In the BizTalk Server Administration console specify XMLTransmit for the Send pipeline property on a send port. Click the ellipsis to configure the pipeline properties and specify the schema for the envelope in the EnvelopeDocSpecNames property.  
  
  Schema resolution by message type may not work if several versions of the same schema are intentionally or accidentally deployed in the database (for example, in a side-by-side deployment or if multiple scenarios do not have unique message types). If schema resolution by message type fails, a "schema ambiguity" error is added to the event log. To ensure that schema resolution by message type succeeds, do one of the following:  
  
- Define the schemas in the same BizTalk project as your custom pipeline.  
  
- Sign the assembly with the schemas with the same key as the assembly containing the pipelines.  
  
- Explicitly specify schemas in pipeline components (message type names should be unique across the BizTalk Management database).  
  
> [!IMPORTANT]
>  When schemas in the same assembly share a message type, you must not include the schemas in the same pipeline component assembly due to the limitations of ambiguity resolution; instead, reference schemas that are external to the pipeline component assembly. Ambiguity resolution does not work when schemas and pipeline components are in the same assembly, even if schema type names are explicitly specified in pipeline components in custom pipelines.  
  
> [!NOTE]
>  Custom pipeline components that use **IPipelineContext** to obtain deployed schemas should obtain schemas by schema type only if the schema type name is not specified for the component at run time, and obtain schemas by message type only if the schema type information is not available when the component is run.  
  
## See Also  
 [Pipeline Components](../core/pipeline-components.md)