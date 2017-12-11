---
title: "Converting Data Types from OS-390 COBOL to Automation1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 877e79d1-8fc2-4d31-bbc8-10c255d0fb23
caps.latest.revision: 3
---
# Converting Data Types from OS/390 COBOL to Automation
Use the tables in this topic as a guide when you set up the way you want Transaction Integrator (TI) to handle conversions from COBOL data types to Automation data types. For more information about the specific data types, see [Supported TI Data Types](../HIS2010/supported-ti-data-types1.md).  
  
 Use the following code key to interpret the codes in the **Possible Conversion Errors** and **Required Property Settings** columns in each table.  
  
|Code|Description|  
|----------|-----------------|  
|r|Range errors possible.|  
|b|Possible loss of precision due to base 2 to base 16 conversion.|  
|p|Possible loss of precision due to picture format scale specification.|  
|m|Mapping errors possible.|  
|f|yyyyddd and hhmmss.|  
|A|You must specify **Truncate**, **Round**, or **Error** under **Error handling** on the **COBOL Definition** tab of the property page.|  
|C|You must specify the precision and scale by filling in the **Digits left** and **Digits right** boxes on the **COBOL Definition** tab of the property page.|  
|D|You must specify the string width by filling in the **Size** box on the **COBOL Definition** tab of the property page.|  
|E|Unicode or EBCDIC mapping information is required, such as a code page.|  
|F|For arrays whose length is less than the maximum specified, you must specify **Size of Filler** under **Trailing filler** on the **COBOL Definition** tab of the property page.|  
|G|You must specify how strings should be dealt with. Click **Space Padded** or **Null terminated** under **String Delimiting** on the **COBOL Definition** tab of the property page. Then click **Truncate** or **Error** under **Error handling** on the **COBOL Definition** tab of the property page to specify what TI should do if the string is too long.|  
|H|Maximum size is required.|  
|I|Localization is required.|  
|J|Optional SO and SI insertion and deletion is supported.|  
  
 The following table shows the defaults that TI uses when you import COBOL source code.  
  
### Default  
  
|From OS/390 COBOL data type|To Automation data type|Possible conversion errors|Required property settings|  
|----------------------------------|-----------------------------|--------------------------------|--------------------------------|  
|COMP-1|4-byte Real (Single)|b,r|None|  
|COMP-2|8-byte Real (Double)|b,r|None|  
|COMP-3 Packed Decimal|Currency|p|AC|  
|COMP-3 Packed Decimal|Decimal|p|AC|  
|DATE and TIME|Date|None|I|  
|TIME only|Date|None|I|  
|DATE only|Date|None|I|  
|PIC X|Variable-length String|m|DEG|  
|PIC X No Translation|1-byte unsigned Integer|None|None|  
|PIC S9(4) COMP (Integer 16-bit)|2-byte signed Integer|None|None|  
|PIC S9(4) COMP (Integer 16-bit)|Boolean|None|None|  
|PIC S9(9) COMP (Integer 32-bit)|4-byte signed Integer|None|None|  
|OCCURS fixed TIMES|Array|None|None|  
  
> [!NOTE]
>  When you convert fractional numbers from Packed Decimal or distributed program call (DPC) Zoned Decimal data types, you should convert to Visual Basic Decimal data type.  
  
 For COMP, COMP-3, and DISPLAY numeric COBOL data types, the default is based on the precision and scale shown in the following table. When COBOL uses DISPLAY without a sign and you change the Automation type to String, the COBOL picture is changed to PIC X, which has the same internal data representation. The length remains the same and therefore does not affect your mainframe program.  
  
|Precision and scale for OS/390 COBOL|To Automation data type|  
|-------------------------------------------|-----------------------------|  
|Precision 1-4, scale 0|2-byte signed Integer|  
|Precision 5-9, scale 0|4-byte signed Integer|  
|Precision 5-7, scale 3-7|4-byte Real|  
|Precision 8-18, scale 3-18|8-byte Real|  
|Precision 1-18, scale 1-2|Currency|  
|Precision 10-18, scale 0|Decimal|  
  
 The following table shows the other supported data type mappings that you can set in TI Project to override the defaults presented previously in this topic.  
  
### Supported in Transaction Integrator  
  
|From OS/390 COBOL data type|To Automation data type|Possible conversion errors|Required property settings|  
|----------------------------------|-----------------------------|--------------------------------|--------------------------------|  
|COMP-1|Array|None|None|  
|COMP-2|Array|None|None|  
|COMP-3 Packed Decimal|2-byte signed Integer|p,r|AC|  
|COMP-3 Packed Decimal|4-byte signed Integer|p,r|AC|  
|COMP-3 Packed Decimal|4-byte Real (Single)|p,r|AC|  
|COMP-3 Packed Decimal|8-byte Real (Double)|p|C|  
|COMP-3 Packed Decimal|Boolean|None|None|  
|COMP-3 Packed Decimal|1-byte unsigned Integer|r|None|  
|COMP-3 Packed Decimal|Array|None|None|  
|DISPLAY Zoned Decimal|2-byte signed Integer|p,r|AC|  
|DISPLAY Zoned Decimal|4-byte Real (Single)|p,r|AC|  
|DISPLAY Zoned Decimal|8-byte Real (Double)|p,r|AC|  
|DISPLAY Zoned Decimal|Currency|p,r|AC|  
|DISPLAY Zoned Decimal|Decimal|p,r|AC|  
|DATE and TIME|Array|None|None|  
|TIME only|Array|None|None|  
|DATE only|Array|None|None|  
|PIC X|Array|None|None|  
|PIC X No Translation|Array|None|None|  
|PIC G|Variable-length String|m|DEGJ|  
|PIC G|Array|None|None|  
|PIC S9(4) COMP (Integer 16-bit)|1-byte unsigned Integer|r|None|  
|PIC S9(4) COMP (Integer 16-bit)|Array|None|None|  
|PIC S9(9) COMP (Integer 32-bit)|Boolean|None|None|  
|PIC S9(9) COMP (Integer 32-bit)|1-byte unsigned Integer|r|None|  
|PIC S9(9) COMP (Integer 32-bit)|Array|None|None|  
PIC S9(?)V9(?) COMP (16-bit)|4-byte Real (Single)|p,r|None|  
|PIC S9(?)V9(?) COMP (16-bit)|8-byte Real (Double)|p,r|None|  
|PIC S9(?)V9(?) COMP (16-bit)|Currency|p,r|None|  
|PIC S9(?)V9(?) COMP (16-bit)|Decimal|p,r|None|  
|PIC S9(?)V9(?) COMP (32-bit)|4-byte Real (Single)|p,r|None|  
|PIC S9(?)V9(?) COMP (32-bit)|8-byte Real (Double)|p,r|None|  
PIC S9(?)V9(?) COMP (32-bit)|Currency|p,r|None|  
|PIC S9(?)V9(?) COMP (32-bit)|Decimal|p,r|None|  
|OCCURS DEPENDING ON|Array|None|None|  
  
> [!NOTE]
>  When you convert fractional numbers from Packed Decimal or DPC Zoned Decimal data types, you should convert to Visual Basic Decimal data type.  
  
 The following table shows additional supported data type mappings that the TI run-time environment supports.  
  
### Supported only by the TI run-time environment  
  
|From OS/390 COBOL data type|To Automation data type|Possible conversion errors|Required property settings|  
|----------------------------------|-----------------------------|--------------------------------|--------------------------------|  
|DISPLAY Zoned Decimal|1-byte unsigned Integer|None|AC|  
|DISPLAY Zoned Decimal|4-byte signed Integer|None|AC|  
|DISPLAY Zoned Decimal|Boolean|None|AC|  
  
 No other data type conversions from COBOL to Automation are supported by TI at this time.  
  
## See Also  
 [Supported TI Data Types](../HIS2010/supported-ti-data-types1.md)   
 [Converting Data Types from Automation to OS/390 COBOL\]](../HIS2010/converting-data-types-from-automation-to-os-390-cobol]1.md)   
 [Data Type Conversion](../HIS2010/data-type-conversion2.md)