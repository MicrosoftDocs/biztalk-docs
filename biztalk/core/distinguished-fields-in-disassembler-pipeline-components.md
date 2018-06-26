---
title: "Distinguished Fields in Disassembler Pipeline Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components, distinquished fields"
  - "Flat File Disassembler [pipeline component], distinquished fields"
  - "BizTalk Framework Disassembler [pipeline component], distinquished fields"
  - "XML Disassembler [pipeline component], distinquished fields"
ms.assetid: 7e51d2fe-0004-4a7b-9055-bd41e8a4b7ab
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Distinguished Fields in Disassembler Pipeline Components
Distinguished fields defined in a schema are written to the message context by the XML Disassembler, BizTalk Framework Disassembler, or Flat File Disassembler pipeline components in the following format:  
  
 *name used* is the distinguished field in XPath  
  
 *namespace URI* is "<http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields>"  
  
 The value of the property is the **System.String** value extracted from the XML document using specified XPath.  
  
 The following example schema has a distinguished field Price.  
  
```  
<?xml version="1.0" encoding="utf-16" ?>   
<xs:schema xmlns="http://SendHtmlMessage.PO" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://SendHtmlMessage.PO xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="PO">  
      <xs:annotation>  
         <xs:appinfo>  
            <b:properties>  
               <b:property distinguished="true" xpath="/*[local-name()='PO' and namespace-uri()='http://SendHtmlMessage.PO']/*[local-  
               name()='Price' and namespace-uri()='']" />   
            </b:properties>  
         </xs:appinfo>  
      </xs:annotation>  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="Item" type="xs:string" />   
            <xs:element name="Price" type="xs:string" />   
         </xs:sequence>  
      </xs:complexType>  
   </xs:element>  
</xs:schema>  
```  
  
 For the document instance  
  
```  
<PO>  
            <Item>Bolt</Item>  
            <Price>10</Price>  
<PO>  
```  
  
 the XML Disassembler writes a distinguished field on a message context as follows:  
  
 Name of the property on the context: `"/*[local-name()='PO' and namespace-uri()='http://SendHtmlMessage.PO']/\*[local-name()='Price' and namespace-uri()='']"`  
  
 Namespace of the property: http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields  
  
 Value of the property: 10  
  
> [!NOTE]
>  If the size of any XML document element values exceeds 85KB, a degradation in the performance of processing those documents may occur.  
  
## See Also  
 [Flat File Disassembler Pipeline Component](../core/flat-file-disassembler-pipeline-component.md)   
 [How to Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)
