---
description: "Learn more about: Configuration Property Variable Types"
title: "Configuration Property Variable Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapters, properties"
  - "binding files, properties"
  - "binding files, data types"
  - "adapters, data types"
ms.assetid: 703219ce-e275-4a07-a2ad-28010d8363e6
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuration Property Variable Types
The adapter configuration properties in a TransportTypeData\CustomProps node of a binding file adhere to the data types available in the .NET Framework VarEnum enumeration. Relevant data types are listed in the table below:  
  
|Member Name|Description|Value|  
|-----------------|-----------------|-----------|  
|VT_EMPTY|Indicates that a value was not specified.|0|  
|VT_NULL|Indicates a null value, similar to a null value in SQL.|1|  
|VT_I2|Indicates a short integer.|2|  
|VT_I4|Indicates a long integer.|3|  
|VT_R4|Indicates a float value.|4|  
|VT_R8|Indicates a double value.|5|  
|VT_CY|Indicates a currency value.|6|  
|VT_DATE|Indicates a DATE value.|7|  
|VT_BSTR|Indicates a BSTR string.|8|  
|VT_DISPATCH|Indicates an IDispatch pointer.|9|  
|VT_ERROR|Indicates an SCODE.|10|  
|VT_BOOL|Indicates a Boolean value.|11|  
|VT_VARIANT|Indicates a VARIANT far pointer.|12|  
|VT_UNKNOWN|Indicates an IUnknown pointer.|13|  
|VT_DECIMAL|Indicates a decimal value.|14|  
|VT_I1|Indicates a char value.|16|  
|VT_UI1|Indicates a byte.|17|  
|VT_UI2|Indicates an unsigned short.|18|  
|VT_UI4|Indicates an unsigned long.|19|  
|VT_I8|Indicates a 64-bit integer.|20|  
|VT_UI8|Indicates an 64-bit unsigned integer.|21|  
|VT_CLSID|Indicates a class ID.|72|  
|VT_ARRAY|Indicates a SAFEARRAY pointer.|8192|  
|VT_BYREF|Indicates that a value is a reference.|16384|
