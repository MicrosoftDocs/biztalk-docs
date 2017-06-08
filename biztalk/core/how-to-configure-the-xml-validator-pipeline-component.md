---
title: "How to Configure the XML Validator Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML Validator [pipeline component]"
  - "send pipelines, validating"
  - "pipeline components, XML Validator"
  - "receive pipelines, validating"
ms.assetid: 3b3becaf-703c-4399-a5ed-e7082e31e6e9
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the XML Validator Pipeline Component
The XML Validator pipeline component can be used in any stage (except Disassemble or Assemble) in a send or receive pipeline.  
  
### To configure the properties for the XML Validator pipeline component  
  
1.  Drag the XML Validator pipeline component into the Validate stage of a receive pipeline.  
  
2.  In the Properties window, in the **Pipeline Component Properties** section, set the following.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Document schemas**|Indicates the namespace and typename of the schema or schemas to be applied to the document. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md). If no schemas are specified, the run-time schema discovery will be done by using the message's target namespace and root element name information. **Note:**  You may receive a "Two or more of the selected schema share the same target namespace" error if you specify two or more schemas for the **Document schemas** property. <br /><br /> Default value: Empty collection|  
    |Recoverable Interchange Processing|When "false" - indicates that entire interchange is validated as a unit (if any contained message fails, entire interchange is suspended).<br /><br /> When "true" - indicates that messages within interchange are extracted individually by validator with possibility of some propagating through messaging pathway and others being suspended.<br /><br /> For more information on recoverable interchange processing, see [Recoverable Interchange Processing](../core/recoverable-interchange-processing.md).|  
  
## See Also  
 [XML Validator Pipeline Component](../core/xml-validator-pipeline-component.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)