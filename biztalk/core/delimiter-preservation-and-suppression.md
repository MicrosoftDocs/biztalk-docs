---
title: "Delimiter Preservation and Suppression | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30985b94-625e-411a-8137-1c129bc197bf
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Delimiter Preservation and Suppression

## Overview
There are two properties that apply to delimited records: **Preserve Delimiter For Empty Data** and **Suppress Trailing Delimiters**. Use these properties to control how the flat file assembler handles delimiters associated with nonexistent data and trailing delimiters. When you set the **Preserve Delimiter For Empty Data** property to **Yes** (which is the default setting), delimiters are included in the translated flat file message for:  
  
- Fields without data.  
  
- Immediately subordinate records without data that do not have a tag associated with them.  
  
  When you set the **Preserve Delimiter For Empty Data** property to **No**, delimiters are not included in the translated flat file for records and fields without data. Further, regardless of the setting of the **Preserve Delimiter For Empty Data** property, delimiters will not be included in the translated flat file message for immediately subordinate records without data for which a tag is defined.  
  
  When you set the **Suppress Trailing Delimiters** property to **No** (which is the default setting), one or more trailing delimiters may be included in the translated flat file message. When you set the **Suppress Trailing Delimiters** property to **Yes**, trailing delimiters are not included in the translated flat file message.  

## Special scenarios  
 There are some special cases where the behaviors caused by the settings of the **Preserve Delimiter For Empty Data** and **Suppress Trailing Delimiters** properties can conflict. In such cases, the behaviors associated with the latter property, **Suppress Trailing Delimiters**, will take precedence. Further, there are some special cases where you will be warned about potential conflicts between the settings you have chosen for these two properties.  
  
 For example, consider a **Record** node defined with the following property values:  
  
- Node Name is MyRec  
  
- Tag Identifier is Rec  
  
- Child Delimiter is ,  
  
- Child Order is Infix  
  
  And defined to contain five **Field Element** nodes with the following names (they could also be **Field Attribute** nodes or subordinate **Record** nodes):  
  
- FieldElem1  
  
- FieldElem2  
  
- FieldElem3  
  
- FieldElem4  
  
- FieldElem5  
  
  Next, assume that the following mainly empty XML fragment, representing this **Record** node, is passed to the flat file assembler.  
  
```  
<MyRec>  
    <FieldElem1 />  
    <FieldElem2 />  
    <FieldElem3>Val</FieldElem3>  
    <FieldElem4 />  
    <FieldElem5 />  
</MyRec>  
  
```  
  
 The following table shows the output produced, and the associated additional property setting requirements for the relevant schema nodes, based on different settings for the **Preserve Delimiter For Empty Data** (PDFED) and **Suppress Trailing Delimiters** (STD) properties.  
  
|PDFED setting|STD setting|Output|Additional node requirements|  
|---|---|---|---|  
|Yes|No|Rec,,,Val,,|None.|  
|No|Yes|Rec,Val|All **Field Element** nodes must be configured as optional.|  
|Yes|Yes|Rec,,,Val|Nodes named **FieldElem4** and **FieldElem5** must be configured as optional.|  
|No|No|Rec,Val,,|All **Field Element** nodes must be configured as optional.|  
  
 When these property settings specify that delimiters should either not be preserved or should be suppressed, a message warning that it might not be possible to parse the serialized flat file data using the same schema will be issued in the following two cases:  
  
-   When the **Record** node for which the **Preserve Delimiter For Empty Data** property is set to **No** and/or the **Suppress Trailing Delimiters** property is set to **Yes**, respectively, contains subordinate **Field Element** nodes, **Field Attribute** nodes, or **Record** nodes for which no tag is specified.  
  
-   When the subordinate **Field Element** nodes, **Field Attribute** nodes, and **Record** nodes for which no tag is specified are not configured to be optional (by setting the **Min Occurs** property set to zero) in the schema. When the **Suppress Trailing Delimiters** property is set to **Yes**, only the last such subordinate nodes need to be configured as optional. When the **Preserve Delimiter For Empty Data** property is set to **No**, all trailing subordinate nodes need to be configured as optional.  
  
> [!NOTE]
>  Delimiters are always preserved when the XML element associated with a (presumably optional) **Record**, **Field Element**, or **Field Attribute** node are entirely missing from the XML representation of the business document except when a Record follows a missing optional Field. In other words, when the data and its surrounding XML tags are both missing, the corresponding delimiter is always included in the flat file representation of the business document.  
  
 Now change the schema to include a child record with two Field Element immediately following a missing Field Element. The child record elements are configured to use the &#124; (pipe) character as a delimiter.  
  
```  
<MyRec>  
    <FieldElem1 />  
    <FieldElem2 />  
    <FieldElem3>Val</FieldElem3>  
    <!-- <FieldElem4 /> -->  
    <ChildRec>  
        <InnerFieldElement1>Inner1</InnerFieldElement1>   
        <InnerFieldElement2>Inner2</InnerFieldElement1>  
    </ChildRec>  
    <FieldElem5 />  
</MyRec>  
  
```  
  
 If this is passed to the flat file disassembler, the delimiters for FieldElem4 will not be preserved but subsequent records will be delimited as expected.  
  
```  
,,Val,,Inner1,Inner2,,  
```  
  
## See Also  
- [Delimited Record Considerations](../core/delimited-record-considerations.md)   
- **Preserve Delimiter For Empty Data (Node Property of Flat File Schemas)** and **Suppress Trailing Delimiters (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
