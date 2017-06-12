---
title: "XML Validator Pipeline Component Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.BizTalk.Component.XmlValidator"
  - "Microsoft.BizTalk.PipelineComponents.XmlValidator"
ms.assetid: fc10c053-9878-4a66-aa89-b21a81068adc
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XML Validator Pipeline Component Properties
Use the XML validator pipeline component to verify the message against the specified schema or schemas. If the message does not conform to these schemas, the component raises an error and the message is placed in the suspended queue by the messaging engine.  
  
 The XML validator pipeline component is intended for use in any stage (except disassemble or assemble) in a Send or Receive pipeline.  
  
 The properties of the XML validator pipeline component can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable XML validator pipeline component properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Document schemas**|Indicate the namespace and typename of the schema or schemas to be applied to the document. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md). If no schemas are specified, the runtime schema discovery will use the message's target namespace and root element name information.<br /><br /> Default value: Empty collection (Collection)|  
|**Recoverable interchange processing**|Indicate whether to process messages within an interchange individually. For more information, see [Recoverable Interchange Processing](../core/recoverable-interchange-processing.md)<br /><br /> Default Value: False|  
  
## See Also  
 [Using Pipeline Designer](../core/using-pipeline-designer.md)   
 [How to Configure the XML Validator Pipeline Component](../core/how-to-configure-the-xml-validator-pipeline-component.md)   
 [XML Validator Pipeline Component](../core/xml-validator-pipeline-component.md)