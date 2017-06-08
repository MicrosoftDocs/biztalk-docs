---
title: "Property Schema Base (Node Property of Property Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Property Schema Base property [property schemas]"
ms.assetid: 5cd7da90-1a6b-4a2b-8e29-ee2a9b60d1d9
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Property Schema Base (Node Property of Property Schemas)
Use the **Property Schema Base** property to specify the origin of the data associated with the selected **Field Element** node. The data can originate in either the instance message itself or from another source, such as the envelope in which the instance message is enclosed.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md)  
  
## Category  
 Reference  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**MessageDataPropertyBase**|Use this value to specify that the value associated with the selected **Field Element** node originates from a promoted property within an associated document schema.|  
|**MessageContextPropertyBase**|Use this value to specify that the value associated with the selected **Field Element** node may or may not originate from a promoted property within an associated document schema.<br /><br /> Most built-in BizTalk Server context properties are of this type, as well as values that originate in the envelope portion of an incoming instance message.|  
|**PartContextPropertyBase**|Use this value to specify the runtime that the value for the property will be part of the MessagePart context.|  
|**(Default)**|Removes the corresponding annotation in the XSD representation of the schema, if any, resulting in the same behavior as the **MessageDataPropertyBase** setting.|  
  
## Default Value  
 **(Default)**, resulting in no corresponding annotation in the XSD representation of the schema, and producing the same behavior as the **MessageDataPropertyBase** setting.  
  
## XSD Persistence  
 As the value of the **propSchFieldBase** (="MessageDataPropertyBase" or "MessageContextPropertyBase") attribute of the **element/annotation/appinfo/fieldInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you are editing a property schema and you select a **Field Element** node in BizTalk Editor.  
  
 When this property is set to **MessageDataPropertyBase** for the selected **Field Element** node, it references its value in the instance message using an XPath. Furthermore, in order for the selected **Field Element** node value to be accessible to orchestrations, some node in the corresponding document schema must be promoted to this **Field Element** node.  
  
 When this property is set to **MessageContextPropertyBase** for the selected **Field Element** node, its value is always available within orchestrations, regardless of any property promotions in the corresponding document schema.  
  
## See Also  
 [Supplemental Node Properties for Property Schemas](../core/supplemental-node-properties-for-property-schemas.md)