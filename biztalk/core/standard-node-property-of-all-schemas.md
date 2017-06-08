---
title: "Standard (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Standard property [schemas]"
ms.assetid: 90378ade-fe27-42a2-bd25-0682ec51b65e
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Standard (Node Property of All Schemas)
Use the **Standard** property to define the format and/or syntax of the instance messages that the schema being edited defines.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Reference  
  
## Allowed Values  
 Any string, though it is often one of the choices from the drop-down list or one of several well-known industry standards such as "X12" or "EDIFACT".  
  
 The following table shows the drop-down list choices for the **Standard** property.  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**XML**|Sets the **standard** attribute to "XML", specifying that the selected schema defines the structure of XML instance messages.|  
|**(Default)**|Removes the **standard** attribute, if present, which is equivalent to specifying that the selected schema defines the structure of XML instances messages (same as **XML**).|  
|**Flat File**|Specifies that the schema defines the structure of flat file instance messages.<br /><br /> This choice is only available when the **Flat File Extension** has been enabled using the **Schema Editor Extensions** property. When this extension is enabled, the **Standard** property is automatically set to **Flat File**.|  
|**EDI**|Specifies that the schema defines the structure of EDI instance messages.<br /><br /> This choice is only available when the **EDI Schema Editor Extension** has been enabled using the **Schema Editor Extensions** property. When this extension is enabled, the **Standard** property is automatically set to **EDI**.|  
  
 New schema editor extensions may add new choices to this drop-down list.  
  
## Default Value  
 **(Default)**, specifying that the selected schema defines the structure of XML instances messages.  
  
## XSD Persistence  
 As the value of the **standard** attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Schema** node in BizTalk Editor.  
  
 If you set more than one schema editor extension, the automatic setting of this property may not be what you intend. It is a good idea to verify manually that this property is set to the proper value for your circumstances.  
  
 Use the [Standard Version](../core/standard-version-node-property-of-all-schemas.md) property to qualify your setting of the **Standard** property with a particular version of that standard.  
  
 If you intend to use the CodeList feature, you should avoid using the period character (".") in the string you provide for this property. For additional information about this restriction, see [CodeList (Node Property of All Schemas)](../core/codelist-node-property-of-all-schemas.md) and [CodeList Database (Node Property of All Schemas)](../core/codelist-database-node-property-of-all-schemas.md).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)   
 [Standard Version (Node Property of All Schemas)](../core/standard-version-node-property-of-all-schemas.md)