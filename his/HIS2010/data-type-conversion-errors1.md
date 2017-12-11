---
title: "Data Type Conversion Errors1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b2ade8a-5341-47f4-8093-be6579b7c96c
caps.latest.revision: 4
---
# Data Type Conversion Errors
A message indicating that a data type conversion could not take place uses a numeric code to identify the data type. The following tables translate the numeric codes into their equivalent variant data types (for Visual C++) and Automation data types (for Visual Basic).  
  
|Numeric Code|Variant Data Type|Automation Data Type|  
|------------------|-----------------------|--------------------------|  
|0x0000|VT_EMPTY|nothing|  
|0x0002|VT_I2|2-byte signed int|  
|0x0003|VT_I4|4-byte signed int|  
|0x0004|VT_R4|4-byte real|  
|0x0005|VT_R8|8-byte real|  
|0x0006|VT_CY|currency|  
|0x0007|VT_DATE|date|  
|0x0008|VT_BSTR|OLE Automation string|  
|0x0009|VT_DISPATCH|IDispatch * (currently only for recordset pointer)|  
|0x000b|VT_BOOL|True=-1, False=0|  
|0x000c|VT_VARIANT|VARIANT *|  
|0x000e|VT_DECIMAL|16-byte fixed point|  
|0x0011|VT_UI1|unsigned char|  
|0x0018|VT_VOID|C style void|  
|0x001b|VT_SAFEARRAY|(use VT_ARRAY in VARIANT)|  
|0x001d|VT_USERDEFINED|user-defined type|  
  
 Arrays of the following types have these codes:  
  
|Numeric Code|Variant Data Type|Automation Data Type|  
|------------------|-----------------------|--------------------------|  
|0x2000|VT_EMPTY|nothing|  
|0x2002|VT_I2|2-byte signed int|  
|0x2003|VT_I4|4-byte signed int|  
|0x2004|VT_R4|4-byte real|  
|0x2005|VT_R8|8-byte real|  
|0x2006|VT_CY|currency|  
|0x2007|VT_DATE|date|  
|0x2008|VT_BSTR|OLE Automation string|  
|0x2009|VT_DISPATCH|IDispatch * (currently only for recordset pointer)|  
|0x200b|VT_BOOL|True=-1, False=0|  
|0x200c|VT_VARIANT|VARIANT *|  
|0x200e|VT_DECIMAL|16-byte fixed point|  
|0x2011|VT_UI1|unsigned char|  
|0x2018|VT_VOID|C style void|  
|0x201b|VT_SAFEARRAY|(use VT_ARRAY in VARIANT)|  
|0x201d|VT_USERDEFINED|user-defined type|  
  
 The following types are passed by reference:  
  
|Numeric Code|Variant Data Type|Automation Data Type|  
|------------------|-----------------------|--------------------------|  
|0x4000|VT_EMPTY|nothing|  
|0x4002|VT_I2|2-byte signed int|  
|0x4003|VT_I4|4-byte signed int|  
|0x4004|VT_R4|4-byte real|  
|0x4005|VT_R8|8-byte real|  
|0x4006|VT_CY|currency|  
|0x4007|VT_DATE|date|  
|0x4008|VT_BSTR|OLE Automation string|  
|0x4009|VT_DISPATCH|IDispatch * (currently only for recordset pointer)|  
|0x400b|VT_BOOL|True=-1, False=0|  
|0x400c|VT_VARIANT|VARIANT *|  
|0x400e|VT_DECIMAL|16-byte fixed point|  
|0x4011|VT_UI1|unsigned char|  
|0x4018|VT_VOID|C style void|  
|0x401b|VT_SAFEARRAY|(use VT_ARRAY in VARIANT)|  
|0x401d|VT_USERDEFINED|user-defined type|  
  
 Arrays of the following types are passed by reference:  
  
|Numeric Code|Variant Data Type|Automation Data Type|  
|------------------|-----------------------|--------------------------|  
|0x6000|VT_EMPTY|nothing|  
|0x6002|VT_I2|2-byte signed int|  
|0x6003|VT_I4|4-byte signed int|  
|0x6004|VT_R4|4-byte real|  
|0x6005|VT_R8|8-byte real|  
|0x6006|VT_CY|currency|  
|0x6007|VT_DATE|date|  
|0x6008|VT_BSTR|OLE Automation string|  
|0x6009|VT_DISPATCH|IDispatch * (currently only for recordset pointer)|  
|0x600b|VT_BOOL|True=-1, False=0|  
|0x600c|VT_VARIANT|VARIANT *|  
|0x600e|VT_DECIMAL|16-byte fixed point|  
|0x6011|VT_UI1|unsigned char|  
|0x6018|VT_VOID|C style void|  
|0x601b|VT_SAFEARRAY|(use VT_ARRAY in VARIANT)|  
|0x601d|VT_USERDEFINED|user-defined type|