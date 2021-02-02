---
description: "Learn more about: Parsing Modes"
title: "Parsing Modes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components [custom], code samples"
  - "pipeline components [custom], parsing"
ms.assetid: b1188720-e5ae-47ae-ab8e-16d7ed08b778
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Parsing Modes
The parsing mode is an attribute on the schemaInfo record, with two modes: speed and complexity. The Parser Optimization property can be configured within the BizTalk Schema Editor.  
  
## Example  
  
```  
<b:schemaInfo count_positions_by_byte="false" standard="Flat File"   
root_reference="document" parser_optimization="complexity" />.  
```  
  
 In speed mode, the parser tries to fit data as they appear in the stream. For example, given the following schema.  
  
```  
<schema>  
   Root ("," prefix)  
      Field1   opt  
      Field2   opt  
      Field3   opt  
      Field4   opt  
      Record ("," infix)  
            Field5  
            Field6  
</schema>  
```  
  
 and input message.  
  
```  
,1,2,3,4  
```  
  
 with speed mode the following XML document is obtained.  
  
```  
<Root>  
   <Field1>1</Field1>  
   <Field2>2</Field2>  
   <Field3>3</Field3>  
   <Field4>4</Field4>  
</Root>  
```  
  
 With complexity mode, the same schema produces the following output.  
  
```  
<Root>  
   <Field1>1</Field1>  
   <Field2>2</Field2>  
      <Record>  
         <Field5>3</Field5>  
         <Field6>4</Field6>  
      </Record>  
</Root>  
```  
  
 In complexity mode, the flat file parsing engine uses both top-down and bottom-up parsing, and tries to fit data more accurately. In speed mode, the parser tries to fit data as they appear in the stream.  
  
 If you have optional elements with required elements, for example.  
  
```  
<schema>  
   Root  
      Record1 (required)  
  
      Record2 (optional)  
  
      Record3 (required)  
  
```  
  
 you must use complexity mode to correctly parse the data, because the parser represents the schema internally as.  
  
```  
<schema>  
   Root  
      Record1 (required)  
      <sequence> (optional)  
         Record2 (required)  
         Record3 (required)  
```  
  
## See Also  
 [Using the Flat File Parsing Engine](../core/using-the-flat-file-parsing-engine.md)
