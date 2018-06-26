---
title: "DbDataReader class in the Siebel adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Data Provider for Siebel, DbDataReader"
  - "DbDataReader"
ms.assetid: 7673cd10-ec1e-4cb0-93c2-f11928d00ca2
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# DbDataReader class in the Siebel adapter
The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] provides a `DbDataReader` leveraging the XML Data Reader. This provides the consumer of the Siebel data source the ability to read a forward-only stream of rows.  

## Supported Properties  
 The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports the following `DbDataReader` properties.  

|Name|Get/Set|Description|  
|----------|--------------|-----------------|  
|**HasRows**|Get|This property is not supported, and will throw an exception if accessed.|  
|**IsClosed**|Get|Gets a value indicating whether the `DbDataReader` is closed.|  
|**RecordsAffected**|Get|Gets a value indicating whether the `DbDataReader` contains one or more rows.|  
|**Item(Int32)**|Get|Gets the value of the specified column as an instance of Object. Use the ordinal number for the desired column when invoking this indexer.|  
|**Item(String)**|Get|Gets the value of the specified column as an instance of Object. Use the name of the desired column when invoking this indexer.|  

## Supported Methods  
 The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports the following `DbDataReader` methods.  


|        Name        |                                                                                                                                                                                                                            Description                                                                                                                                                                                                                             |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **GetSchemaTable** | Returns a `DataTable` that describes the column metadata of the `DbDataReader`. The schema column attributes supported by the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] are:<br /><br /> -   ColumnName<br />-   ColumnOrdinal<br />-   .NET DataType<br />-   Length<br />-   Precision (if available)<br />-   Scale (if available)<br />-   AllowDBNull<br />-   LocalName<br />-   Extended LocalName<br />-   Namespace |
|   **GetString**    |                                                                                                                                                                                                 Gets the value of the specified column as an instance of `String`.                                                                                                                                                                                                 |
|    **GetValue**    |                                                                                                                                                                                                 Gets the value of the specified column as an instance of `String`.                                                                                                                                                                                                 |
|    **isDbNull**    |                                                                                                                                                                                       Gets a value that indicates whether the column contains nonexistent or missing values.                                                                                                                                                                                       |
|   **NextResult**   |                                                                                                                                                           The Siebel Data Provider always returns a single result set; hence this call fully exhausts the current result set before returning **false**.                                                                                                                                                           |
|      **Read**      |                                                                                                                                                         Advances the reader to the next record in a result set.  It returns **true** if it succeeds, and **false** if the reader has no more records left.                                                                                                                                                         |
|     **Close**      |                                                                                                         Closes the `DbDataReader` object. **Caution:**  When you are done using the `DbDataReader` object, you must close it, in order to free up the Siebel COM library objects. Otherwise, the client application’s memory and handle usage will go up.                                                                                                          |

## See Also  
 [Extend ADO.NET Interfaces with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)