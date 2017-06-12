---
title: "Grid Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "grid properties [BizTalk Mapper]"
  - "properties, grid [BizTalk Mapper]"
  - "grid properties [BizTalk Mapper], about grid properties"
ms.assetid: 0478cd4a-3786-4b90-9e37-6dc64797e018
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Grid Properties
Grid properties are displayed in the Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you click in the background of a grid page. These properties control global aspects of how a map is created and compiled. Many of these properties, specifically those in the Custom Header category, correspond to attributes of the XSL **output** element, allowing you to specify options for use in serializing the transformation output.  
  
> [!NOTE]
>  Grid properties apply to the grid as a whole, and not to the individual pages in the grid. In other words, if you set a grid property on one grid page, and then set the same property when a different grid page is showing, you are setting the same single property, and not two different instances of the same property.  
  
 The following table describes grid properties.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
||||  
|[CDATA Section Elements](../core/cdata-section-elements-grid-property.md)|Custom Header|Specifies a list of elements whose text node children should be output by using CDATA sections.<br /><br /> Provides a value for the **cdata-section-elements** attribute of the XSL **output** element.|  
|[Copy Processing Instructions (PIs)](../core/copy-processing-instructions-pis-grid-property.md)|Custom Header|Specifies whether any processing instructions found in the source instance message should be copied to the destination instance message during transformation.|  
|[Custom Extension XML](../core/custom-extension-xml-grid-property.md)|Compiler|Specifies the custom extension XML file, if any.|  
|[Custom XSLT Path](../core/custom-xslt-path-grid-property.md)|Compiler|Specifies the custom XSLT file, if any.|  
|[Doctype Public](../core/doctype-public-grid-property.md)|Custom Header|Specifies the public identifier to be used in the DTD.<br /><br /> Provides a value for the **doctype-public** attribute of the XSL **output** element.|  
|[Doctype System](../core/doctype-system-grid-property.md)|Custom Header|Specifies the system identifier to be used in the DTD.<br /><br /> Provides a value for the **doctype-system** attribute of the XSL **output** element.|  
|[Ignore Namespaces for Links](../core/ignore-namespaces-for-links-grid-property.md)|General|Specifies whether the links stored in the map contain any references to the namespaces used in the schemas.|  
|[Indent](../core/indent-grid-property.md)|Custom Header|Specifies whether the XML in destination instance messages produced by using this map will be indented for improved readability.<br /><br /> Provides a value for the **indent** attribute of the XSL **output** element.|  
|[Media-Type](../core/media-type-grid-property.md)|Custom Header|Specifies the media type (Multipurpose Internet Mail Extensions (MIME) content type) of the data in the output of the transformation.<br /><br /> Provides a value for the **media-type** attribute of the XSL **output** element.|  
|[Method](../core/method-grid-property.md)|Custom Header|Specifies the overall method for producing the result tree.|  
|[Omit XML Declaration](../core/omit-xml-declaration-grid-property.md)|Custom Header|Specifies whether the transformation output should include an XML declaration.<br /><br /> Provides a value for the **omit-xml-declaration** attribute of the XSL **output** element.|  
|[Script Type Precedence](../core/script-type-precedence-grid-property.md)|Compiler|Opens the **Script Type Precedence** dialog box, in which you can configure the relative precedence of the various types of script.|  
|[Source Schema](../core/source-schema-grid-property.md)|General|Shows the relative path to the chosen source schema.|  
|[Standalone](../core/standalone-grid-property.md)|Custom Header|Specifies whether the XSLT processor should output a stand-alone document declaration.<br /><br /> Provides a value for the **standalone** attribute of the XSL **output** element.|  
|[Target Schema](../core/target-schema-grid-property.md)|General|Shows the relative path to the chosen destination schema.<br /><br /> **Note:** In Microsoft BizTalk® Server, "target" and "destination" are used interchangeably with respect to schemas and instance messages.|  
|[Version](../core/version-grid-property.md)|Custom Header|Specifies version "1.0" in relation to the "xml" output method, which appears in the output XML declaration as:<br /><br /> `<?xml version='1.0' ?>`<br /><br /> Provides a value for the **version** attribute of the XSL **output** element.|  
|[XSLT Encoding](../core/xslt-encoding-grid-property.md)|Custom Header|Specifies the preferred character encoding that the parser should use to encode sequences of characters as sequences of bytes.<br /><br /> Provides a value for the **encoding** attribute of the XSL **output** element.|