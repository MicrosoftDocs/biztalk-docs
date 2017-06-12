---
title: "Process Contents (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Process Contents property [schemas]"
ms.assetid: 0e1660e6-e2f5-402c-88ca-5fda990eb855
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Process Contents (Node Property of All Schemas)
Use the **Process Contents** property to specify the level of validation for the selected **Any Element** or **Any Attribute** node.  
  
## Applies to Nodes of Type  
 [Any Element](../core/any-element-node-properties.md), [Any Attribute](../core/any-attribute-node-properties.md)  
  
## Category  
 General  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Use this to clear the property field of other values and to remove the **processContents** attribute from the corresponding **any** or **anyAttribute** element in the XSD representation. When you select this option, the default behavior associated with the **Strict** setting is used.|  
|**Lax**|Specifies that validation should be loosely applied to the elements or attributes found in the position of the corresponding **any** or **anyAttribute** element, respectively, in the XSD representation by setting its **processContents** attribute to "lax". With this setting, validation is only performed if the corresponding element or attribute declaration is found in the schema.|  
|**Skip**|Specifies that validation should not occur for the elements found in the position of the corresponding **any** or **anyAttribute** element, respectively, in the XSD representation by setting its **processContents** attribute to "skip".|  
|**Strict**|Specifies that validation should be strictly applied to the elements found in the position of the corresponding **any** or **anyAttribute** element, respectively, in the XSD representation by setting its **processContents** attribute to "strict".|  
  
## Default Value  
 **(Default)**, resulting in the behavior associated with the **Strict** setting.  
  
## XSD Persistence  
 As the value of the **processContents** attribute of the corresponding **any** or **anyAttribute** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select an **Any Element** or **Any Attribute** node in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 You should generally set this property value to **Skip** to successfully validate XML documents containing elements that are represented by the corresponding **Any Element** or **Any Attribute** node. Other setting combinations are summarized in the table below:  
  
|\<xs:any> Setting|Intent|Comments|  
|------------------------|------------|--------------|  
|\<xs:any processContents="strict"/>|Allow any element from any namespace with strict validation.|You must import the different schemas that may appear as an element. If you do not, validation will fail because the element is not declared.|  
|\<xs:any processContent="lax"/>|Allow any element from any namespace with lax validation.|Elements belonging to schemas that have been imported will be validated while all others will be skipped. If you forget to import a schema, validation will succeed.|  
|\<xs:any processContent="skip"/>|Allow any element from any namespace skipping any validation.|Validation for all elements will be skipped.|  
|\<xs:any processContents="strict" namespace="http://mynamespace"/>|Allow elements from a specific namespace with strict validation.|You must import the schemas that may appear as an element. If you do not, validation will fail because the element is not declared.|  
|\<xs:any processContents="strict" namespace="##Other"/>|Allow elements from any schema other than the one containing this \<xs:any> tag.|You must import the schemas that may appear as an element. If you do not, validation will fail because the element is not declared.|  
|<xs:any processContents="strict" namespace="http://mynamespace "<br /><br /> minOccurs="1" maxOccurs="50"/>|Allow 1 to 50 elements from a specific namespace with strict validation.|You must import the schemas that may appear as an element. If you do not, validation will fail because the element is not declared.|  
  
 There are some combinations of elements that, when used with the **Any** element, may cause the content model to become ambiguous. For example, if your schema contains an element with a maxOccurs constraint prior to an **Any** element, you must qualify the **Any** element with a namespace:  
  
```  
<xs:element ref="ns0:Automobile" maxOccurs="10"/>  
<xs:any namespace="http://mynamespace" processContents="lax"/>   
```  
  
> [!NOTE]
>  Make sure you understand the impact of the **Any** element within your schema and make accommodations as needed.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)