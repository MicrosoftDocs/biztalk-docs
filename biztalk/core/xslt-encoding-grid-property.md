---
title: "XSLT Encoding (Grid Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XSLT Encoding property [grid pages]"
ms.assetid: 9e206d6d-55f4-41bf-a46a-29e33fe324fd
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XSLT Encoding (Grid Property)
Use the **XSLT Encoding** property to specify the preferred character encoding that the parser should use to encode sequences of characters as sequences of bytes.  
  
## Category  
 Custom Header  
  
## Allowed Values  
  
|Value|Description|  
|-----------|-----------------|  
|None|Specifies that no value should be set for the **encoding** attribute of the **\<xsl:output>** element.|  
|Hard-coded encoding choices in drop-down list|The drop-down list includes many common encoding choices, such as UTF-8.|  
|Other valid encoding choices|Any freeform values that you type here are unverified by BizTalk Mapper. You must ensure their validity.|  
  
## Default Value  
 None  
  
## Remarks  
 If you type a value for this property, it is treated case-insensitively; it must contain only printable ASCII characters and be a registered character set, or begin with x-.  
  
 This property provides a value for the **encoding** attribute of the XSL **output** element. For more information about this attribute, refer to the .NET Framework documentation.  
  
> [!NOTE]
>  You cannot undo or redo the **XSLT Encoding** property.  
  
## See Also  
 [Grid Properties](../core/grid-properties.md)