---
title: "Basic Oracle Data Types in the Oracle EBS adapter in BizTalk | Microsoft Docs"
description: Data and XSD types, safe typing, and validation in the Oracle e-Business Suite in the BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 008bf621-8b4e-450d-b354-ee26b91592f2
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Basic Oracle Data Types
This topic describes how the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] surfaces basic Oracle data types.  
  
## Supported Oracle Data Types  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports safe typing for some Oracle data types. When safe typing is enabled, these data types are represented as strings. You configure safe typing by enabling the **EnableSafeTyping** binding property (disabled by default). For more information about the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
> [!NOTE]
>  Safe typing is not supported if data types are inside User Defined Types (UDTs).  
  
 The following table shows how the Oracle data types are surfaced with safe typing disabled (**EnableSafeTyping** is **false**). Oracle data types that are affected by the **EnableSafeTyping** binding property are marked with an asterisk (*).  
  
|Oracle Data Type|XSD type|.NET type|Comments|  
|----------------------|--------------|---------------|--------------|  
|BFile|input: xsd:string<br /><br /> output: xsd:base64Binary|String<br /><br /> Byte[]|BFile data type is not supported inside complex types (such as RecordType, TableType, UDT, and VArray).|  
|Blob|xsd:base64Binary|Byte[]|-|  
|Char|xsd:string|String|-|  
|Clob|xsd:string|String|-|  
|Date*<br /><br /> (No safe typing if inside an UDT)|xsd:dateTime|DateTime|Date values cannot contain time zone information (UTC or UTC offsets):<br /><br /> -   xsd:dateTime values must not contain UTC or UTC offsets<br />-   **DateTime.Kind** must be **DateTimeKind.Unspecified**<br /><br /> If time zone information is specified, the adapter throws an **XmlReaderParsingException** exception with a message that indicates the field. **Note:**  The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes Oracle Date data type as xsd:dateTime instead of xsd:date because: <ul><li>Oracle Date data type can also contain time value.</li><li>There is no .NET equivalent for xsd:date.</li></ul>|  
|Float**|xsd:float if prec <=7<br /><br /> xsd:double if prec > 7 and <=15<br /><br /> xsd:string if prec > 15|Float<br /><br /> Double<br /><br /> String|You must specify the value consistent with the format specified for the decimal character and group separator in the **NumericCharacters** binding property under the **MlsSettings** binding property. If no value is specified for the **NumericCharacters** binding property, the adapter uses the MLS settings for the ODP.NET client on the same computer where the adapter is installed.|  
|IntervalDS|xsd:string<br /><br /> xsd:duration if inside an UDT|String<br /><br /> Timespan if inside an UDT|The adapter returns the IntervalDS data as a string using the OracleIntervalDS.ToString method.<br /><br /> The value should be expressed in Oracle native format: Day HH:MI:SSxFF (for example, "5 15:30:12.99").|  
|IntervalYM|xsd:string<br /><br /> xsd:long if inside an UDT|String<br /><br /> Long if inside an UDT|The adapter returns the IntervalYM data as a string using the OracleIntervalYM.ToString method.<br /><br /> The value should be expressed in Oracle native format: Year-Month; for example, "1-2" (1 year and 2 months).|  
|Long|xsd:string|String|Starting with the Oracle database 9i release, the LONG data type is deprecated. Oracle recommends using the Large Object (LOB) data types instead. Therefore, when performing operations on the Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], we recommend using Oracle database artifacts that operate on LOB data types and not the LONG data type.|  
|LongRaw|xsd:base64Binary|Byte[]|-|  
|NChar|xsd:string|String|-|  
|NClob|xsd:string|String||  
|Number**|xsd:decimal if prec <=28<br /><br /> xsd:string if prec > 28|Decimal<br />String|-|  
|NVarchar2|xsd:string|String|-|  
|Raw|xsd:base64Binary|Byte[]||  
|RowID|xsd:string|String|-|  
|TimeStamp*<br /><br /> (No safe typing if inside an UDT)|xsd:dateTime if prec <= 7<br /><br /> xsd:string if prec > 7|DateTime<br /><br /> String|When exposed as string (prec > 7), the value should be expressed in Oracle NLS_TIMESTAMP_FORMAT. You can specify the string format for TimeStamp data types in the **TimeStampFormat** binding property under the **MlsSettings** binding property. If no value is specified for the **TimeStampFormat** binding property, the adapter uses the MLS settings for the ODP.NET client on the same computer where the adapter is installed.<br /><br /> TimeStamp values cannot contain time zone information (UTC or UTC offsets):<br /><br /> -   xsd:dateTime values must not contain UTC or UTC offsets<br />-   **DateTime.Kind** must be **DateTimeKind.Unspecified**<br /><br /> If time zone information is specified, the adapter throws an **XmlReaderParsingException** exception with a message that indicates the field.|  
|TimeStampLTZ|xsd:string|String|TimeStampLTZ is not supported inside UDTs.<br /><br /> **Outside an UDT**: The value should be expressed in Oracle NLS_TIMESTAMP_TZ_FORMAT. You can specify the string format for TimeStampLTZ data types in the **TimeStampTZFormat** binding property under the **MlsSettings** binding property. If no value is specified for the **TimeStampTZFormat** binding property, the adapter uses the MLS settings for the ODP.NET client on the same computer where the adapter is installed.|  
|TimeStampTZ|xsd:string<br /><br /> xsd:dateTime if inside an UDT|String<br /><br /> DateTime if inside an UDT|**Outside an UDT**: The value should be expressed in Oracle NLS_TIMESTAMP_TZ_FORMAT. You can specify the string format for TimeStampTZ data types in the **TimeStampTZFormat** binding property under the **MlsSettings** binding property. If no value is specified for the **TimeStampTZFormat** binding property, the adapter uses the MLS settings for the ODP.NET client on the same computer where the adapter is installed.|  
|Decimal**|xsd:decimal if prec <=28<br /><br /> xsd:string if prec > 28|Decimal<br /><br /> String|-|  
|Varchar2|xsd:string|String|-|  
|Binary Float**|xsd:float if prec <=7<br /><br /> xsd:string if prec > 7|Float<br /><br /> String|You must specify the value consistent with the format specified for the decimal character and group separator in the **NumericCharacters** binding property under the **MlsSettings** binding property. If no value is specified for the **NumericCharacters** binding property, the adapter uses the MLS settings for the ODP.NET client on the same computer where the adapter is installed.|  
|Binary Double**|xsd:double if prec <=15<br /><br /> xsd:string if prec > 15|Double<br /><br /> String|-|  
|Binary Integer**|xsd:integer|Int32||  
|Boolean|xsd:boolean|Nullable boolean||  
|XMLTYPE|xsd:string|String|Supported for top level procedure parameters.<br /><br /> Reserved XML characters like ‘**\<**’, ‘**\>**’ must be replaced with their entity representation **(&lt;, &gt;)** when developing applications in BizTalk, and when using WCF channel Model. This is not required in the case of WCF Service Model.|  
  
 \*The way in which these Oracle data types are surfaced is affected by the **EnableSafeTyping** binding property.  
  
 \*\*The way in which these Oracle numeric data types inside DataSets and weakly-typed REF CURSORS are surfaced is affected by the **EnableSafeTyping** binding property.  
  
> [!IMPORTANT]
>  -   The maximum length of the value in an Oracle data type in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is bound by the maximum length of the value supported by ODP.NET for the Oracle data type.  
> -   The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] internally treats the Oracle numeric data types inside UDTs as .NET Decimal. However, in general (that is outside UDTs), the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] internally treats the Oracle numeric data types as OracleDecimal.  
  
## Safe Typing Enabled  
 The following table shows how the Oracle data types that are affected by safe typing are changed when the **EnableSafeTyping** binding property is **true**.  
  
> [!NOTE]
>  Oracle data types that are not in this table are surfaced in the same way whether safe typing is enabled or disabled.  
  
|Oracle Data Type|XSD type|.NET type|Comment|  
|----------------------|--------------|---------------|-------------|  
|Date|xsd:string|String|The value should be expressed in Oracle NLS_DATE_FORMAT. You can specify the format for the Date data types in the **DateFormat** binding property under the **MlsSettings** binding property. If no value is specified for the **DateFormat** binding property, the adapter uses the MLS settings for the ODP.NET client on the same computer where the adapter is installed.|  
|TimeStamp|xsd:string|String|The value should be expressed in Oracle NLS_TIMESTAMP_FORMAT. You can specify the string format for TimeStamp data types in the **TimeStampFormat** binding property under the **MlsSettings** binding property. If no value is specified for the **TimeStampFormat** binding property, the adapter uses the MLS settings for the ODP.NET client on the same computer where the adapter is installed.|  
  
> [!IMPORTANT]
>  If safe typing is enabled, the Oracle numeric data types inside DataSets and weakly-typed REF CURSORS are always exposed as strings.  
  
## Validation  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] performs no explicit validation on the values that you specify for Oracle data types. However, depending on the Oracle data type and whether safe typing is enabled or disabled, implicit validation may be performed:  
  
-   When de-serializing between the XML passed in a message and the .NET types that are used internally by the adapter.  
  
-   By ODP.NET for some data types.  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)