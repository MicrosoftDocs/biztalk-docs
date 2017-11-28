---
title: "Basic Oracle Data Types1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data types, supported"
  - "data types, unsupported"
ms.assetid: 491230b9-b946-4681-a048-5da46102c370
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Basic Oracle Data Types
This topic describes how the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces basic Oracle data types.  
  
## Supported Oracle Data Types  
 The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports safe typing for some Oracle data types. When safe typing is enabled, these data types are represented as strings. You configure safe typing by setting the **EnableSafeTyping** binding property. Safe typing is disabled by default. For more information about the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
> [!NOTE]
>  Safe typing is not supported if data types are inside User Defined Types (UDTs).  
  
 The following table shows how the Oracle data types are surfaced with safe typing disabled (**EnableSafeTyping** is false). Oracle data types that are affected by the **EnableSafeTyping** binding property are marked with an asterisk (*).  
  
|Oracle Data Type|XSD type|.NET type|Comments|  
|----------------------|--------------|---------------|--------------|  
|BFile|input: xsd:string<br />output: xsd:base64Binary|String<br />Byte[]|BFile data type is not supported inside complex types (such as RecordType, TableType, UDT, and VArray).|  
|Blob|xsd:base64Binary|Byte[]|Supported for table operations and procedures.|  
|Char|xsd:string|String|Supported for table operations and procedures.|  
|Clob|xsd:string|String|Supported for table operations and procedures.|  
|Date*<br /><br /> (No safe typing if inside an UDT)|xsd:dateTime|DateTime|Date values cannot contain time zone information (UTC or UTC offsets):<br /><br /> -   xsd:dateTime values must not contain UTC or UTC offsets<br />-   **DateTime.Kind** must be **DateTimeKind.Unspecified**<br /><br /> If time zone information is specified, the adapter throws an **XmlReaderParsingException** exception with a message that indicates the field.|  
|Float**|xsd:float if prec <=7<br />xsd:double if prec > 7 and <=15<br />xsd:string if prec > 15|Float<br />Double<br />String|-|  
|IntervalYM|xsd:string<br /><br /> xsd:long if inside an UDT|String<br /><br /> Long if inside an UDT|The value should be expressed in Oracle native format: Year-Month; For example, "1-2" (1 year and 2 months).|  
|IntervalDS|xsd:string<br /><br /> xsd:duration if inside an UDT|String<br /><br /> Timespan if inside an UDT|The value should be expressed in Oracle native format: Day HH:MI:SSxFF; for example, "5 15:30:12.99"|  
|Long|xsd:string|String|Supported for all table operations, stored procedures, and functions. **Note:**  Starting with the Oracle database 9i release, the LONG data type is deprecated. Oracle recommends using the LOB data types instead. Hence, when performing operations on the Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], we recommend using Oracle database artifacts that operate on LOB data types and not the LONG data type.|  
|LongRaw|xsd:base64Binary|Byte[]|-|  
|NChar|xsd:string|String|-|  
|NClob|xsd:string|String|Supported for table operations and procedures.|  
|Number**|xsd:decimal if prec <=28<br />xsd:string if prec > 28|Decimal<br />String|-|  
|NVarchar2|xsd:string|String|-|  
|Raw|xsd:base64Binary|Byte[]|Supported for table operations and procedures.|  
|RowID|xsd:string|String|-|  
|TimeStamp*<br /><br /> (No safe typing if inside an UDT)|xsd:dateTime if prec <= 7<br />xsd:string if prec > 7|DateTime<br />String|TimeStamp values cannot contain time zone information (UTC or UTC offsets):<br /><br /> -   xsd:dateTime values must not contain UTC or UTC offsets<br />-   **DateTime.Kind** must be **DateTimeKind.Unspecified**<br /><br /> If time zone information is specified, the adapter throws an **XmlReaderParsingException** exception with a message that indicates the field.|  
|TimeStampLTZ|xsd:string|String|TimeStampLTZ is not supported inside UDTs.<br /><br /> **Outside an UDT**: The value should be expressed in NLS_TIMESTAMP_TZ_FORMAT.|  
|TimeStampTZ|xsd:string<br /><br /> xsd:dateTime if inside an UDT|String<br /><br /> DateTime if inside an UDT|**Outside an UDT**: The value should be expressed in NLS_TIMESTAMP_TZ_FORMAT.|  
|Decimal**|xsd:decimal if prec <=28<br />xsd:string if prec > 28|Decimal<br />String|-|  
|Varchar2|xsd:string|String|-|  
|Binary Float**|xsd:float if prec <=7<br />xsd:string if prec > 7|Float<br />String|You must specify the value in a form consistent with your locale (**System.Globalization.CultureInfo.CurrentCulture**). For example, for English locale use a period character (‘.’) to specify the decimal; for French locale, use a comma character (‘,’).|  
|Binary Double**|xsd:double if prec <=15<br />xsd:string if prec > 15|Double<br />String|-|  
|Binary Integer**|xsd:integer|Int32|Supported for procedures, functions, and packages.|  
|Boolean|xsd:boolean|Nullable boolean||  
|XMLTYPE|xsd:string|String|Supported for top level procedure parameters.<br /><br /> Reserved XML characters like ‘**\<**’, ‘**\>**’ must be replaced with their entity representation **(&lt;, &gt;)** when developing applications in BizTalk, and when using WCF channel Model. This is not required in the case of WCF Service Model.|  
  
 \*The way in which these Oracle data types are surfaced is affected by the **EnableSafeTyping** binding property.  
  
 \*\*The way in which these Oracle numeric data types inside DataSets and weakly-typed REF CURSORS are surfaced is affected by the **EnableSafeTyping** binding property.  
  
> [!IMPORTANT]
>  -   The maximum length of the value in an Oracle data type in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is bound by the maximum length of the value supported by ODP.NET for the Oracle data type.  
> -   The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] internally treats the Oracle numeric data types inside UDTs as .NET Decimal. However, in general (that is outside UDTs), the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] internally treats the Oracle numeric data types as OracleDecimal.  
  
### Safe Typing Enabled  
 The following table shows how the Oracle data types that are affected by safe typing are changed when the **EnableSafeTyping** binding property is true.  
  
|Oracle Data Type|XSD type|.NET type|Comment|  
|----------------------|--------------|---------------|-------------|  
|Date|xsd:string|String|The value should be expressed in Oracle NLS_DATE_FORMAT.|  
|TimeStamp|xsd:string|String|The value should be expressed in Oracle NLS_TIMESTAMP_FORMAT.|  
  
> [!IMPORTANT]
>  If safe typing is enabled, the Oracle numeric data types inside DataSets and weakly-typed REF CURSORS are always exposed as strings.  
  
 Oracle data types that are not in this table are surfaced in the same way whether safe typing is enabled or disabled.  
  
### Validation  
 The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] performs no explicit validation on the values that you specify for Oracle data types. However, depending on the Oracle data type and whether safe typing is enabled or disabled, implicit validation may be performed:  
  
-   When de-serializing between the XML passed in a message and the .NET types that are used internally by the adapter.  
  
-   By ODP.NET for some data types.  
  
