---
title: "Basic Siebel Data Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Siebel data types, supported"
ms.assetid: bf86f639-6c45-49db-9e58-79c3ad2c9978
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Basic Siebel Data Types
This section describes how Siebel data types are supported on the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].  

## Supported Siebel Data Types  
 The following table shows the Siebel data types that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] supports and how they are represented by the adapter for BizTalk (XSD type) and in the WCF service model (.NET type). For the types marked with an asterisk, see the note following the table.  


|     Data Type     |    XSD type    | .NET type |                                                                                                                                                                                                                                                                                                                                                                             Description                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------|----------------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    DTYPE_BOOL     |  xsd:boolean   |  Boolean  |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|  DTYPE_CURRENCY   |  xsd:decimal   |  Decimal  |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|    DTYPE_DATE     | xsd:dateTime\* | DateTime  | The value must not be Coordinated Universal Time (UTC).<br /><br /> -   For xsd:dateTime, values are expected to follow this pattern: "(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.\*)".<br />-   For **DateTime** objects,**DateTime.Kind** must be **DateTimeKind.Unspecified**.<br /><br /> The time component will be ignored by the adapter.<br /><br /> For outbound messages, the adapter performs a runtime validation to ensure that the value specified is not UTC (z or UTC offset). If that validation fails, the adapter throws an exception.<br /><br /> When this type is exposed as xsd:string (based on rules explained below):<br /><br /> -   The format is determined by the underlying database.<br />-   No runtime validation is performed on the value. |
|  DTYPE_DATETIME   | xsd:dateTime\* | DateTime  |                                                                                          The value can contain both date and time components and must not be UTC.<br /><br /> -   For **DateTime** objects, **DateTime.Kind** must be **DateTimeKind.Unspecified**.<br /><br /> For outbound messages, the adapter performs a run-time validation to ensure that these conditions are met; if the validation fails, the adapter throws an exception.<br /><br /> When this type is exposed as xsd:string (based on rules explained below):<br /><br /> -   The format is determined by the underlying database.<br />-   No run-time validation is performed on the value.                                                                                           |
|     DTYPE_ID      |   xsd:string   |  String   |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|   DTYPE_INTEGER   |    xsd:int     |   Int32   |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|    DTYPE_NOTE     |   xsd:string   |  String   |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|   DTYPE_NUMBER    |  xsd:decimal   |  Decimal  |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|    DTYPE_PHONE    |   xsd:string   |  String   |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|    DTYPE_TEXT     |   xsd:string   |  String   |                                                                                                                                                                                                                                                                                                                                                                                  -                                                                                                                                                                                                                                                                                                                                                                                   |
|    DTYPE_TIME     | xsd:dateTime\* | DateTime  |                                       The value must not be UTC.<br /><br /> -   For xsd:dateTime, values are expected to follow this pattern: (1753-01-01)T(\d\d:\d\d:\d\d)(.\*)".<br />-   For **DateTime** objects<strong>, DateTime.Kind</strong> must be **DateTimeKind.Unspecified**.<br /><br /> For outbound messages, the adapter performs a runtime validation to ensure that the value specified is not UTC (z or UTC offset). If that validation fails, the adapter throws an exception.<br /><br /> When this type is exposed as xsd:string (based on the rules explained below):<br /><br /> -   The format is determined by the underlying database.<br />-   No run-time validation is performed on the value.                                       |
| DTYPE_UTCDATETIME | xsd:dateTime\* | DateTime  |                                                   The value can contain both date and time components and must be UTC.<br /><br /> -   For xsd:dateTime, the value must be expressed in UTC ('Z' notation or UTC offset).<br />-   For **DateTime** objects **DateTime.Kind** must be **DateTimeKind.Utc**.<br /><br /> For outbound messages, the adapter performs a run-time validation to ensure that these conditions are met; if the validation fails, the adapter throws an exception.<br /><br /> When this type is exposed as xsd:string (based on rules explained below):<br /><br /> -   The format is determined by the underlying database.<br />-   No run-time validation is performed on the value.                                                   |

 The following are the Business Service method argument types:  

 Date  
 The same as DTYPE_DATE.  

 Number  
 The same as DTYPE_NUMBER.  

 String  
 The same as DTYPE_TEXT.  

 Hierarchy  
 Corresponds to XSD type xsd:string, and to .Net type String.  In XML messages, this has to be placed in a CDATA node.  

 Integration Object  
 The same as Hierarchy.  

 *The adapter determines whether to use xsd:dateTime or xsd:string to represent DTYPE_DATE, DTYPE_DATETIME, DTYPE_TIME, and DTYPE_UTCDATETIME fields in business components in the following manner.  

1.  If the business component field has one of the preceding data types, the adapter will expose it as the xsd:dateTime type (in .Net this maps to the DateTime type).  

2.  If the business component field has no data type, the adapter will expose it as xsd:string (in .Net this maps to the String type).  

## Supported Facets for the XML Schema Types  
 The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] supports the following facets for the XML schema types.  

|Siebel Type|Facet|  
|-----------------|-----------|  
|DTYPE_BOOL|None|  
|DTYPE_CURRENCY|Precision (22), Scale|  
|DTYPE_DATE|(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.*)|  
|DTYPE_DATETIME|None|  
|DTYPE_ID|MaxLength (15)|  
|DTYPE_INTEGER|Precision (22)|  
|DTYPE_NOTE|MaxLength (16384)|  
|DTYPE_NUMBER|Precision (22), Scale|  
|DTYPE_PHONE|MaxLength (40)|  
|DTYPE_TEXT|MaxLength (2048)|  
|DTYPE_TIME|(1753-01-01)T(\d\d:\d\d:\d\d)(.*)|  
|DTYPE_UTCDATETIME|None|  

 The following are some rules that govern how and when the facets, and their values, are published:  

 If the Length attribute of the field is set to a value greater than zero and less than or equal to the maximum value (specified in parentheses in the preceding table):  

-   The Precision facet is published as follows:  

    -   If the Precision attribute is set for the field, the same value is published as Precision facet.  

    -   If the Precision attribute is not set for the field, the Length value is published as the Precision facet.  

-   The Scale facet is published only if both:  

    -   The Precision attribute has been published  

    -   The Scale attribute is set for the field to a value greater than zero and less than the value published as part of the Precision facet  

-   The MaxLength facet is the value specified for the Length attribute. This is picked up from the field definition repository. In case the length is not specified in the field definition repository, the value specified in parentheses in the preceding table gets published.  

### Special Cases Related to Siebel Data Types  
 The following rules affect the business component field facets based on the context of the operation in which they are used. These rules are applicable for INSERT and UPDATE operations only. For QUERY operations, all business component fields are exposed to the user.  

 **Business component field marked as REQUIRED in Siebel**  

 Even if a business component field is marked as REQUIRED in the Siebel system but the pre-default or post-default values are set for the field, [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] marks the field as OPTIONAL. Hence if a user provides a value to be inserted or updated, the adapter processes that value. If no value is provided, Siebel uses the pre-default/post-default values.  

 **Business component field NOT marked as READ ONLY in Siebel**  

 If a business component field is NOT marked as READ ONLY, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposes it as a writable field. However, there are a couple of exceptions to this rule. These are:  

- If the business component field is a **Calculated** field in Siebel, it will not appear in the Insert or Update operations because Siebel will automatically take care of **Calculated** fields.  

- If the business component field is obtained through an explicit join (table join on another table), it is generally read only. However Siebel allows data to be written to this field if it is a picklist field. Hence, if the business component field is from an explicit join and the field is NOT a picklist field, then it will NOT appear in the Insert or Update operations because adapter clients cannot write data into such fields.  

  **Data type of a field not specified in the Business Component**  

  If the data type of a field is not specified in the Business Component, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposes the field metadata using the following heuristics.  

- If the field is a special field (i.e. picklist or join), the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] will look up the mapped field in the destination Business Component. If that field has a type associated with it, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] will expose that as the type of the field. However, if that type is DTYPE_DATE, DTYPE_TIME, DTYPE_DATETIME, or DTYPE_UTCDATETIME, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] will expose the field as the xsd:string type. If the mapped field doesn’t have an associated type, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] will expose the original field as the xsd:string type.  

- If the field is not a picklist or join field, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] will expose it as the xsd:string type.  

  **Data type, field length, or precision of a parent business component is not available**  

  If the data type, length, or field precision of a parent business component (a business component that has a child business component based on picklists or MVLs), the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] obtains the information about the data type, length, precision, and scale from the picklist business component or the MVL business component.  

## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)