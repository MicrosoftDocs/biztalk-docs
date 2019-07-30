---
title: "Converting Data Types from Automation to OS-390 COBOL]2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1590b510-8a90-460a-be29-b75ef8c01848
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Converting Data Types from Automation to OS/390 COBOL]
Use the tables in this topic as a guide to specify how you want TI to handle conversions from Automation data types to COBOL data types. For more information about the specific data types, see [Supported TI Data Types](../core/supported-ti-data-types2.md).  
  
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
|G|You must specify how to deal with strings. Click **Space Padded** or **Null terminated** under **String Delimiting** on the **COBOL Definition** tab of the property page. Then click **Truncate** or **Error** under **Error handling** on the **COBOL Definition** tab of the property page to specify what TI should do if the string is too long.|  
|H|Maximum size is required.|  
|I|Localization is required.|  
|J|Optional SO and SI insertion and deletion is supported.|  
  
 The following table shows the defaults that TI uses for converting Automation data types to COBOL data types.  
  
### Default  
  
|From Automation data type|To OS/390 COBOL data type|Possible conversion errors|Required property settings|  
|-------------------------------|--------------------------------|--------------------------------|--------------------------------|  
|1-byte unsigned Integer|PIC X No Translation|None|None|  
|2-byte signed Integer|PIC S9(4) COMP (Integer 16-bit)|None|None|  
|4-byte signed Integer|PIC S9(9) COMP (Integer 32-bit)|None|None|  
|4-byte Real (Single)|COMP-1|br|None|  
|8-byte Real (Double)|COMP-2|br|None|  
|Boolean|PIC S9(4) COMP (Integer 16-bit)|None|None|  
|Variable-length String|PIC X|m|DEG|  
|Currency|COMP-3 Packed Decimal|pr|C|  
|Date (date and time)|COMP-3 Packed Decimal|pf|CI|  
|Date (date only)|COMP-3 Packed Decimal|pf|CI|  
|Date (time only)|COMP-3 Packed Decimal|pf|CI|  
|Decimal|COMP-3 Packed Decimal|pr|C|  
|Array (any data type)|OCCURS fixed TIMES|None|FH|  
  
> [!NOTE]
>  When you convert whole or fractional numbers from Visual Basic Single or Visual Basic Double data types to Packed Decimal or distributed program call (DPC) Zoned Decimal data types, TI is limited to a precision from 1 through 18 digits left of the decimal point (for example, 1.2345678901234567E+17). When you convert fractional numbers Packed Decimal or DPC Zoned Decimal data types, you should convert to Visual Basic Decimal data type.  
  
 The following table shows the other supported data type mappings that you can set in TI Project to override the defaults presented in the previous table.  
  
### Supported in Transaction Integrator  
  
|From Automation data type|To OS/390 COBOL data type|Possible conversion errors|Required property settings|  
|-------------------------------|--------------------------------|--------------------------------|--------------------------------|  
|1-byte unsigned Integer|PIC S9(4) COMP (Integer 16-bit)|None|None|  
|1-byte unsigned Integer|COMP-3 Packed Decimal|None|C|  
|2-byte signed Integer|COMP-3 Packed Decimal|None|C|  
|2-byte signed Integer|DISPLAY Zoned Decimal|None|C|  
|4-byte signed Integer|COMP-3 Packed Decimal|None|C|  
|4-byte signed Integer|DISPLAY Zoned Decimal|None|C|  
|4-byte Real (Single)|PIC S9(4) COMP (Integer 16-bit)|p,r|None|  
|4-byte Real (Single)|PIC S9(9) COMP (Integer 32-bit)|p,r|None|  
|4-byte Real (Single)|COMP-3 Packed Decimal|p,r|C|  
|4-byte Real (Single)|DISPLAY Zoned Decimal|p,r|C|  
|8-byte Real (Double)|PIC S9(4) COMP (Integer 16-bit)|p,r|None|  
|8-byte Real (Double)|PIC S9(9) COMP (Integer 32-bit)|p,r||  
8-byte Real (Double)|COMP-3 Packed Decimal|p,r|C|  
|8-byte Real (Double)|DISPLAY Zoned Decimal|p,r|C|  
|Boolean|PIC S9(9) COMP (Integer 32-bit)|None|None|  
|Boolean|COMP-3 Packed Decimal|None|C|  
|Variable-length String|PIC G|m|DEGJ|  
|Currency|PIC S9(?)V9(?) COMP (16-bit)|pr|None|  
|Currency|PIC S9(?)V9(?) COMP (32-bit)|pr|None|  
|Currency|DISPLAY Zoned Decimal|pr|C|  
|Decimal|PIC S9(?)V9(?) COMP (16-bit)|pr|None|  
|Decimal|PIC S9(?)V9(?) COMP (32-bit)|pr|None|  
|Decimal|DISPLAY Zoned Decimal|pr|C|  
|Array (any data type)|OCCURS DEPENDING ON|None|FH|  
  
> [!NOTE]
>  When you convert whole or fractional numbers from Visual Basic Single or Visual Basic Double data types to Packed Decimal or DPC Zoned Decimal data types, TI is limited to a precision of 1 to 18 digits left of the decimal point (for example, 1.2345678901234567E+17).  
  
 The following table shows additional supported data type mappings that the TI run-time environment supports.  
  
### Supported only by the TI run-time environment  
  
|From Automation data type|To OS/390 COBOL data type|Possible conversion errors|Required property settings|  
|-------------------------------|--------------------------------|--------------------------------|--------------------------------|  
|1-byte unsigned Integer|PIC S9(9) COMP (Integer 32-bit)|None|None|  
|1-byte unsigned Integer|DISPLAY Zoned Decimal|None|C|  
|Boolean|DISPLAY Zoned Decimal|None|C|  
  
 No other data type conversions from Automation to COBOL are supported by TI at this time.  
  
> [!NOTE]
>  When the COBOL usage is DISPLAY without a sign and you change the Automation type to String, the COBOL picture is changed to PIC X, which has the same internal data representation. The length remains the same and therefore does not affect your mainframe program.  
  
## See Also  
 [Supported TI Data Types](../core/supported-ti-data-types2.md)   
 [Converting Data Types from OS/390 COBOL to Automation](../core/converting-data-types-from-os-390-cobol-to-automation2.md)   
 [Data Type Conversion](../core/data-type-conversion1.md)