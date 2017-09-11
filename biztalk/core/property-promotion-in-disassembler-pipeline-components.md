---
title: "Property Promotion in Disassembler Pipeline Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components, promoting properties"
  - "XML Disassembler [pipeline component], properties"
  - "pipeline components, properties"
  - "promoting properties, disassembler pipeline components"
  - "BizTalk Framework Assembler [pipeline component], properties"
  - "Flat File Disassembler [pipeline component], properties"
ms.assetid: aa37b308-8aa2-45f4-9383-aca4f2c925ce
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Property Promotion in Disassembler Pipeline Components
Property promotion is a process by which a property value is extracted from an XML document by using an XPath expression and placed on the message context so that it can be used for message routing.  
  
 If a promoted property does not have a default or fixed value, the XML field for that property is missing, and the Validate Document Structure property is **False**, the property is not promoted.  
  
 A custom pipeline component can promote multivalued (that is, arrayed) properties. Messages that contain multivalued properties are only supported in content-based routing (CBR) scenarios; they cannot be routed to orchestrations or be used for tracking purposes.  
  
 The XML Disassembler does not promote default or fixed values for an empty element if it has a closing tag. For example, \<field1> is not promoted in the following XML.  
  
```  
<document>  
   <field1></field1>  
</document>  
```  
  
 However, an empty element without a closing tag (as shown in the following example) is promoted.  
  
```  
<document>  
   <field1/>  
</document>  
```  
  
 When reading datetime data from a document and placing it into the context property, if the data is in UTC format, that format is preserved. If the datetime data is in local+offset format, BizTalk Server converts the datetime format to the UTC format that results from adding the offset to the local time. If the datetime format does not specify time zone or UTC format, the time is assumed to be local and is converted to UTC based on the current time zone.  
  
## See Also  
 [XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md)   
 [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)