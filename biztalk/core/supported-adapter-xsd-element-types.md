---
description: "Learn more about: Supported Adapter XSD Element Types"
title: "Supported Adapter XSD Element Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00691a9e-434f-4baa-9a01-b6f452758ab3
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Supported Adapter XSD Element Types
The following table lists the elements supported by the Adapter Framework. When defining a new element in your configuration schema, use any of the following types to replace `string` in the following example:  
  
```  
<xs:element name="uri" type="xs:string">  
```  
  
|Type|XML type|UI behavior|Other specifics|  
|----------|--------------|-----------------|---------------------|  
|string|None|Edit box accepting type only.|Attribute to constrain max/min|  
|normalizedString|None|Edit box accepting type only.|Attribute to constrain max/min|  
|integer|None|Edit box accepting type only.|Attribute to constrain max/min|  
|positiveInteger|None|Edit box accepting type only.|Attribute to constrain max/min|  
|negativeInteger|None|Edit box accepting type only.|Attribute to constrain max/min|  
|nonNegativeInteger|None|Edit box accepting type only.|Attribute to constrain max/min|  
|nonPositiveInteger|None|Edit box accepting type only.|Attribute to constrain max/min|  
|int|None|Edit box accepting type only.|Attribute to constrain max/min|  
|unsignedInt|None|Edit box accepting type only.|Attribute to constrain max/min|  
|long|None|Edit box accepting type only and a decimal.|Attribute to constrain max/min|  
|unsignedLong|None|Edit box accepting type only and a decimal.|Attribute to constraint max/min|  
|short|None|Edit box accepting type only.|Attribute to constrain max/min|  
|unsignedShort|None|Edit box accepting type only.|Attribute to constrain max/min|  
|decimal|None|Edit box accepting type only.|Attribute to constrain max/min|  
|float|None|Edit box accepting type only.|Attribute to constrain max/min|  
|double|None|Edit box accepting type only.|Attribute to constrain max/min|  
|boolean|None|Drop-down list populated with Boolean values.|None|  
|time|None|Edit box accepting type only.|None|  
|dateTime|None|Edit box accepting type only. An ellipsis appears at the end of the field area. Click the ellipsis and the calendar appears.|None|  
|date|None|Edit box accepting type only. An ellipsis appears at the end of the field area. Click the ellipsis and the calendar appears.|None|  
|gMonth|None|Edit box accepting type only.|This value is a string and thus may not perform as expected. Consider using xsd:int types with restrictions to hold the month value instead.|  
|gYear|None|Edit box accepting type only.|This value is a string and thus may not perform as expected. Consider using xsd:int types with restrictions to hold the year value instead.|  
|gYearMonth|None|Edit box accepting type only.|This value is a string and thus may not perform as expected. Consider using xsd:int types with restrictions to hold the year and month value instead.|  
|gDay|None|Edit box accepting type only.|This value is a string and thus may not perform as expected. Consider using xsd:int types with restrictions to hold the day value instead.|  
|gMonthDay|None|Edit box accepting type only.|This value is a string and thus may not perform as expected. Consider using xsd:int types with restrictions to hold the month and day value instead.|  
|Name|None|Edit box accepting type only.|None|  
|NCName|None|Edit box accepting type only.|None|  
|anyURI|None|Edit box accepting type only.|None|  
|Sequence|"Sequence" Schema Element|None|None|  
|Groups|None|A "+" or "-" sign that expands or collapses all fields within the group.<br /><br /> No edit functionality on the right side of the property page.|None|  
|File Name|FileName|An ellipsis appears at the end of the field area. Click the ellipsis and the **Windows FileOpen** dialog box appears, allowing selection of a file.|None|  
|Folder Name|FolderName|An ellipsis appears at the end of the field area. Click the ellipsis and the **Windows Folder Open** dialog box appears allowing selection of a folder.|None|  
|SSO App ID|SSOAppID|Drop-down list populated with the SSO Application list|None|  
|Password|Password|Edit box with "*" appearing instead of clear text.|None|  
  
## See Also  
 [Adapter Design Issues](../core/adapter-design-issues.md)
