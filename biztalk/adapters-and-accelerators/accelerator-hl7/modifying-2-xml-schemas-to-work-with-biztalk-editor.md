---
title: "Modifying 2.XML Schemas to Work with BizTalk Editor | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "2.XML schemas, modifying"
  - "modifying, 2.XML schemas"
ms.assetid: 07316826-84b6-494e-81b9-f64a3d46ffb0
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Modifying 2.XML Schemas to Work with BizTalk Editor
HL7 2.XML schemas require modification to work properly with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]). The following describes how to modify HL7 V2.XML schemas to enable you to use them with BizTalk Editor.  
  
> [!IMPORTANT]
>  The Update2XMLSchema tool performs these steps automatically. See [Update2XMLSchema Tool](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md) for more information.  
> 
> [!NOTE]
>  The **nillable** attribute can occur in a schema on an element. If set to **true**, it indicates that the instance of the parent element can have an **xsi:nil="true"** attribute. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ignores this attribute during compilation and during parsing/serialization.  
  
### To modify 2.XML schemas  
  
1. In the fields.xsd file, you must remove instances of **import** and replace them with **include**. For example, search the fields.xsd file for the following text:  
  
   ```  
   <xsd:import namespace="urn:hl7-org:v2xml" schemaLocation="datatypes.xsd"/>   
   ```  
  
    And change the text to the following:  
  
   ```  
   <xsd:include schemaLocation="datatypes.xsd"/>   
   ```  
  
2. In the segments.xsd file, you must remove all instances of the lines that contain the text processContents="lax". For example, search the segments.xsd file for the following text:  
  
   ```  
   <xsd:any processContents="lax" namespace="##any" minOccurs="0"/>   
   ```  
  
    And  
  
   ```  
   <xsd:any processContents="lax" namespace="##any"/>   
   ```  
  
    And remove those lines.  
  
3. For all schemas, under the tag xsd:schema, you must add the following line:  
  
   > [!NOTE]
   >  Do not add this line if you have added the schema using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] because [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] does this for you automatically.  
  
   ```  
   xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
   ```  
  
    For example, in the file ADT_A01.xsd, search for the following text:  
  
   ```  
   <xsd:schema  
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
    xmlns="urn:hl7-org:v2xml"   
    targetNamespace="urn:hl7-org:v2xml">   
   ```  
  
    And change the text to the following:  
  
   ```  
   <xsd:schema  
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:hl7-org:v2xml"  
    targetNamespace="urn:hl7-org:v2xml"  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003">   
   ```  
  
4. For all schemas, you must add a root reference. For example, in the ADT_A01.xsd file, search for the following text:  
  
   ```  
   <xsd:include schemaLocation="segments.xsd" />   
   ```  
  
    And change the text to:  
  
   ```  
   <xsd:include schemaLocation="segments.xsd" />  
   <xsd:annotation>   
     <xsd:appinfo>   
       <schemaInfo root_reference="ADT_A01"  
    xmlns="http://schemas.microsoft.com/BizTalk/2003" />   
     </xsd:appinfo>   
   </xsd:annotation>   
   ```  
  
   > [!NOTE]
   >  If you are using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you can add this root_reference by using the following procedure.  
  
### To add the root reference  
  
1.  In Solution Explorer, double-click the schema you want to edit.  
  
2.  In the Properties pane, scroll down to the property **root_reference**, and from the drop-down list, click the property with the same schema name.  
  
3.  On the **File** menu, click **Save All**.  
  
## See Also  
 [Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)