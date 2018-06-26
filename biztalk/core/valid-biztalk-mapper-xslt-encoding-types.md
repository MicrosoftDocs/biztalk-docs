---
title: "Valid BizTalk Mapper XSLT Encoding Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "grid properties"
  - "Code Page property"
  - "XSLT Encoding property [grid pages]"
  - "Schema node"
  - "XSLT, encoding types [BizTalk Mapper]"
  - "BizTalk Mapper, XSLT encoding"
ms.assetid: 922b46cb-7bc8-4267-bf52-e5f0262b8da1
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Valid BizTalk Mapper XSLT Encoding Types
BizTalk Mapper supports different types of Extensible Stylesheet Language Transformations (XSLT) encoding. You use the **XSLT Encoding** grid property to set the XSLT encoding type that you prefer. The following list shows the encoding formats that are available in the drop-down list associated with the **XSLT Encoding** grid property:  
  
- None  
  
- Arabic (windows-1256)  
  
- Baltic (windows-1257)  
  
- Central European (windows-1250)  
  
- Chinese (GB18030)  
  
- Cyrillic (windows-1251)  
  
- Greek (windows-1253)  
  
- Hebrew (windows-1255)  
  
- Japanese (Shift_JIS)  
  
- Korean (ks_c_5601-1987))  
  
- Little Endian Unicode (UTF-16)  
  
- Simplified Chinese (GBK)  
  
- Thai (windows-874)  
  
- Traditional Chinese (Big5)  
  
- Turkish (windows-1254)  
  
- UTF-8  
  
- Vietnamese (windows-1258)  
  
- Western European (windows-1252)  
  
  If you do not find the encoding you want to use in this list, you can enter a different encoding value. Make sure the value you provide is valid because BizTalk Mapper does not test that value.  
  
> [!NOTE]
>  The **Code Page** property of the **Schema** node defines the encoding format for the schemas that you use in maps. To configure the **Code Page** property, open the schema in BizTalk Editor and specify the value of the **Code Page** property.  
  
## See Also  
 [Maps](../core/maps.md)   
 [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md)