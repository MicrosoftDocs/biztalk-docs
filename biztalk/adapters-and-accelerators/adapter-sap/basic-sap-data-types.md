---
title: "Basic SAP Data Types in the mySAP adapter in BizTalk | Microsoft Docs"
description: Supported ABAP and database data types for the mySAP adapter in BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 296b4813-f175-4a02-8fd3-227ae301bc3d
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Basic SAP Data Types
The parameter types that the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports are governed by the:  

- ABAP data types that SAP supports  

- Database data types that SAP supports  

  This section presents a mapping between the ABAP and database data types, and their corresponding .NET and XML schema types.  

> [!NOTE]
>  The information in this section applies to RFCs, tRFCs, and BAPIs. SAP data types are always represented as strings (xsd:string) in IDOCs. This is to support the BizTalk Server flat file parser.  

## Supported ABAP Data Types  
 The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports safe typing for some ABAP data types. When safe typing is enabled, these data types are represented as strings. You configure safe typing by setting the **EnableSafeTyping** binding property. Safe typing is disabled by default. For more information about the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  

 The following table shows how the ABAP data types are surfaced when safe typing is not enabled. (**EnableSafeTyping** is false). Data types that are surfaced differently when safe typing is enabled are marked with an asterisk (*).  

|ABAP Data Type|RFC Type|XSD type|.NET type|Format string|  
|--------------------|--------------|--------------|---------------|-------------------|  
|I (Integer)|RFC_INT|xsd:int|Int32|-|  
|Internal (RFC_INT1)|RFC_INT1|xsd:unsignedByte|Byte|-|  
|Internal (RFC_INT2)|RFC_INT2|xsd:short|Int16|-|  
|F (Float)|RFC_FLOAT|xsd:double|Double|-|  
|P (BCD number)|RFC_BCD|xsd:decimal if length <= 28<br />xsd:string if length > 28|Decimal<br />String|Decimal number. with 0 decimal places<br />Decimal number. with >0 decimal places|  
|C (Character)|RFC_CHAR|xsd:string|String|-|  
|D (Date: YYYYMMDD)*|RFC_DATE|xsd:dateTime|DateTime|Internally, the adapter deserializes the value into a **DateTime** object. It then invokes the **DateTime.ToUniversalTime** method to convert the value of this object to UTC. Finally the date component (**DateTime.Date**) is used to create the value that is sent to the SAP system. The SAP system treats this date value as local time.<br /><br /> You should specify date values as UTC to avoid conversion.<br /><br /> -   For xsd:dateTime, the following pattern is recommended: "(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.\*)Z".<br />-   For **DateTime** objects set **DateTime.Kind** to **DateTimeKind.Utc**.|  
|T (Time: HHMMSS)*|RFC_TIME|xsd:dateTime|DateTime|Internally, the adapter deserializes the value into a **DateTime** object. It then invokes the **DateTime.ToUniversalTime** method to convert the value of this object to UTC. Finally the time component (**DateTime.Time**) is used to create the value that is sent to the SAP system. The SAP system treats this time value as local time.<br /><br /> You should specify time values as UTC to avoid conversion.<br /><br /> -   For xsd:dateTime, the following pattern is recommended: "(0001-01-01)T(\d\d:\d\d:\d\d)(.\*)".<br />-   For **DateTime** objects set **DateTime.Kind** to **DateTimeKind.Utc**.<br /><br /> For example, if your local time is 9:15 am, express this as "(001-01-01)T(09:15:00)Z"|  
|N (Numeric string)*|RFC_NUM|xsd:int if lenrth <= 9<br />xsd:long if length > 9 and <= 19<br />xsd:string if length > 19|Int32<br />long<br />String|-|  
|X (Byte)|RFC_BYTE|xsd:base64Binary|Byte[]|-|  
|STRING|RFC_STRING|xsd:string|String|-|  
|XSTRING|RFC_BYTE|xsd:base64Binary|Byte[]|-|  

 *Indicates that the data type is surfaced differently when safe typing is enabled.  

### Safe Typing Enabled  
 The following table shows the ABAP data types that are surfaced differently when safe typing is enabled (the **EnableSafeTyping** binding property is true).  

|ABAP Data Type|RFC Type|XSD type|.NET type|Format string|  
|--------------------|--------------|--------------|---------------|-------------------|  
|D (Date: YYYYMMDD)|RFC_DATE|xsd:string|String|SAP date format: YYYYMMDD.<br /><br /> Characters are allowed for date digits, so the value is essentially an eight character string|  
|T (Time: HHMMSS)|RFC_TIME|xsd:string|String|SAP time format: HHMMSS.<br /><br /> Characters are allowed for time digits, so the value is essentially a six character string|  
|N (Numeric string)|RFC_NUM|xsd:string|String|An n character string; where n = length of the numc field.|  

 ABAP data types that are not in this table are surfaced in the same way as when safe typing is not enabled.  

### Support for Date and Time Fields  
 When safe typing is not enabled, ABAP Date (D) and Time (T) types are surfaced as xsd:dateTime; however, the pattern facet surfaced for the Date and Time types is different.  

-   The pattern facet for Date is: `(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.*)`  

     For example, July 7, 2007 (2007-07-07) is represented as:  

     `(2007-07-07)T(00:00:00)`.  

-   The pattern facet for Time is: `(0001-01-01)T(\d\d:\d\d:\d\d)(.*)`  

     For example, 18:30:30 (6:30 pm and 30 seconds) is represented as:  

     `(0001-01-01)T(18:30:30)`.  

#### How does the Adapter Represent Minimum and Maximum Time Values on Inbound Messages (from SAP)?  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the following guidelines when it receives time values from the SAP system:  

-   The adapter treats 000000 (hhmmss) and 240000 (hhmmss) as 0 hours, 0 mins, and 0 seconds.  

## Supported Database Data Types  
 The way in which the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces database data types also depends on whether safe typing is enabled. The following table shows how the adapter surfaces database data types when safe typing is not enabled (the **EnableSafeTyping** binding property is false). Data types that are surfaced differently when safe typing is enabled are marked with an asterisk (*).  


|     Database Data Type      |  RFC Type  |                                                                                                                                                                                                                                                                                                              XSD                                                                                                                                                                                                                                                                                                              |                                                     .NET Type                                                      |
|-----------------------------|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
|   ACCP (Posting Period)\*   |  RFC_NUM   |                                                                                                                                                                                                                                                                                                            xsd:int                                                                                                                                                                                                                                                                                                            |                                                       Int32                                                        |
|            CHAR             |  RFC_CHAR  |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|        CLNT (Client)        |  RFC_CHAR  |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|    CURR (Currency field)    |  RFC_BCD   |                                                                                                                                                 xsd:decimal **Note:**  The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] rounds off the decimal values based on the definition of the DECIMAL parameter. For example, if a DECIMAL parameter can accept up to five digits after the decimal point, a value such as 4.000028 is rounded off to 4.00003.                                                                                                                                                  |                                                      Decimal                                                       |
|     CUKY (Currency Key)     |  RFC_CHAR  |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|     DATS (Date field)\*     |  RFC_DATE  |                                                 xsd:dateTime<br /><br /> Internally, the adapter deserializes the value into a **DateTime** object. It then invokes the **DateTime.ToUniversalTime** method to convert the value of this object to UTC. Finally the date component (**DateTime.Date**) is used to create the value that is sent to the SAP system. The SAP system treats this date value as local time.<br /><br /> You should specify date values as UTC to avoid conversion. The following pattern is recommended: "(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.\*)Z".                                                 | DateTime<br /><br /> You should specify date values as UTC (DateTime.Kind = DateTimeKind.Utc) to avoid conversion. |
|        DEC (Amount)         |  RFC_BCD   |                                                                                                                                                 xsd:decimal **Note:**  The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] rounds off the decimal values based on the definition of the DECIMAL parameter. For example, if a DECIMAL parameter can accept up to five digits after the decimal point, a value such as 4.000028 is rounded off to 4.00003.                                                                                                                                                  |                                                      Decimal                                                       |
|    FLTP (Floating point)    | RFC_FLOAT  |                                                                                                                                                                                                                                                                                                          xsd:double                                                                                                                                                                                                                                                                                                           |                                                       Double                                                       |
|            INT1             |  RFC_INT1  |                                                                                                                                                                                                                                                                                                       xsd:unsignedbyte                                                                                                                                                                                                                                                                                                        |                                                        Byte                                                        |
|            INT2             |  RFC_INT2  |                                                                                                                                                                                                                                                                                                           xsd:short                                                                                                                                                                                                                                                                                                           |                                                       Int16                                                        |
|            INT4             |  RFC_INT   |                                                                                                                                                                                                                                                                                                            xsd:int                                                                                                                                                                                                                                                                                                            |                                                       Int32                                                        |
|     LANG (Language Key)     |  RFC_CHAR  |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|            LCHR             | RFC_STRING |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|    LRAW (long byte seq)     |  RFC_BYTE  |                                                                                                                                                                                                                                                                                                       xsd:base64binary                                                                                                                                                                                                                                                                                                        |                                                       Byte[]                                                       |
|           NUMC\*            |  RFC_NUM   |                                                                                                                                                                                                                                                                                             xsd:int<br />xsd:long<br />xsd:string                                                                                                                                                                                                                                                                                             |                  Int32 if length <=9<br />Int64 if length >9 and <=19<br />String if length > 19                   |
|       PREC (Accuracy)       |  RFC_INT2  |                                                                                                                                                                                                                                                                                                           xsd:short                                                                                                                                                                                                                                                                                                           |                                                       Int16                                                        |
|       QUAN (Quantity)       |  RFC_BCD   |                                                                                                                                                 xsd:decimal **Note:**  The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] rounds off the decimal values based on the definition of the DECIMAL parameter. For example, if a DECIMAL parameter can accept up to five digits after the decimal point, a value such as 4.000028 is rounded off to 4.00003.                                                                                                                                                  |                                                      Decimal                                                       |
|     RAW (byte sequence)     |  RFC_BYTE  |                                                                                                                                                                                                                                                                                                       xsd:base64binary                                                                                                                                                                                                                                                                                                        |                                                       Byte[]                                                       |
| RAWSTRING (variable length) |  RFC_BYTE  |                                                                                                                                                                                                                                                                                                       xsd:base64binary                                                                                                                                                                                                                                                                                                        |                                                       Byte[]                                                       |
|  STRING (variable length)   | RFC_STRING |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|     TIMS (Time field)\*     |  RFC_TIME  | xsd:datetime<br /><br /> Internally, the adapter deserializes the value into a **DateTime** object. It then invokes the **DateTime.ToUniversalTime** method to convert the value of this object to UTC. Finally the time component (**DateTime.Time**) is used to create the value that is sent to the SAP system. The SAP system treats this time value as local time.<br /><br /> You should specify time values as UTC to avoid conversion. The following pattern is recommended: "(0001-01-01)T(\d\d:\d\d:\d\d)(.\*)Z".<br /><br /> For example, if your local time is 9:15 am, express this as "(001-01-01)T(09:15:00)Z" | DateTime<br /><br /> You should specify time values as UTC (DateTime.Kind = DateTimeKind.Utc) to avoid conversion. |
|     UNIT (Unit for Qty)     |  RFC_CHAR  |                                                                                                                                                                                                                                                                                                          xsd:string                                                                                                                                                                                                                                                                                                           |                                                       String                                                       |
|        [Unsupported]        |     --     |                                                                                                                                                                                                                                                                                                              --                                                                                                                                                                                                                                                                                                               |                                                       String                                                       |

 *Indicates that the adapter surfaces the data type differently when safe typing is enabled.  

### Safe Typing Enabled  
 The following table shows the database data types that are surfaced differently when safe typing is enabled (the **EnableSafeTyping** binding property is true).  

|Database Data Type|RFC Type|XSD|.NET type|String Value Format|  
|------------------------|--------------|---------|---------------|-------------------------|  
|ACCP (Posting Period)|RFC_NUM|xsd:string|String|Character string|  
|NUMC|RFC_NUM|xsd:string|String|Character string|  
|DATS (Date field)|RFC_DATE|xsd:string|String|YYYYMMDD|  
|TIMS (Time field)|RFC_TIME|xsd:string|String|HHMMSS|  

 Data types that are not in this table are surfaced in the same way as when safe typing is not enabled.  

## Supported XSD Facets  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the following XSD facets.  

|RFC Type|XSD Facet (**EnableSafeTyping** = false)|XSD Facet (**EnableSafeTyping** = true)|  
|--------------|-------------------------------------------------|------------------------------------------------|  
|RFC_BCD|**XSD pattern facet**<br /><br /> **Zero decimal places:** `"([\\-]{0,1})(([0-9]{1,"`  `+ digitsBeforeDecimal +`  `"}))"`<br /><br /> **One or more decimal places:** `"([\\-]{0,1})(([0-9]{0,"` + `digitsBeforeDecimal +``"}\\.[0-9]{0,"``+ digitsAfterDecimal +``"})&#124;([0-9]{1,"``+ digitsBeforeDecimal +``"}))"`|same|  
|RFC_NUM|**XSD totalDigits facet** if length <=19<br /><br /> **XSD pattern facet** if length > 19|**XSD maxLength facet (depends on the length of the value on SAP)**|  
|RFC_DATE|**XSD pattern facet**<br /><br /> `"(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.*)"`<br /><br /> Pattern contains time 00:00:00 to be compatible with `xsd:datetime`|**XSD maxLength facet = 8**|  
|RFC_TIME|**XSD pattern facet**<br /><br /> `"(0001-01-01)T(\d\d:\d\d:\d\d)(.*)"`<br /><br /> Pattern contains date 0001-01-01 to be compatible with `xsd:datetime`|**XSD maxLength facet = 6**|  
|RFC_CHAR|**XSD maxLength facet**|same|  

## Unsupported Data Types  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support the following data type:  

-   ITAB II (hierarchical) table types  

