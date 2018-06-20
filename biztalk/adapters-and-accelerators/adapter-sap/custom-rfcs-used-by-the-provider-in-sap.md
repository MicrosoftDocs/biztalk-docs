---
title: "Custom RFCs Used by the Provider in SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Z_EXTRACT_DATA_OO, limitations related to"
  - "RFC, Z_EXTRACT_DATA_OO"
  - "Z_EXTRACT_DATA_OO"
  - "Z_EXTRACT_DATA_OO, best practice"
  - "Z_EXTRACT_DATA_OO, security issue"
ms.assetid: 95661f4c-0431-40ca-8a53-3fbe359b8afd
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Custom RFCs Used by the Provider in SAP
The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] provides the following custom RFCs that it internally uses to perform operations on the SAP system.  
  
- **Z_EXTRACT_DATA_OO RFC**. The data extraction RFC, Z_EXTRACT_DATA_OO, extracts data from tables or views in the SAP R/3 system, converts the data, and either returns the data synchronously in a SQL Server table or dumps data to a flat file. The Z_EXTRACT_DATA_OO is used to perform SELECT operation with WHERE clauses. The performance of this RFC is dependent on your SAP system hardware.  
  
   For information on how the .NET and SAP data types are mapped for Z_EXTRACT_DATA_OO RFC, see [Data Type Mapping for Custom RFCs](../../adapters-and-accelerators/adapter-sap/data-type-mapping-for-custom-rfcs.md).  
  
- **Z_EXECUTE_SAP_QUERY RFC**. This RFC is used by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] to execute queries that are already defined in the SAP system. This RFC internally executes the SAP RFC, RSAQ_REMOTE_QUERY_CALL. SAP queries are queries that are graphically created using the SAP GUI by selecting the tables, columns, input parameters, sort order of the result set, etc. Using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] you can now execute such SAP queries from an ADO.NET client.  
  
   All values returned by the EXECQUERY operation are of string type.  
  
## Limitations Related to the Z_EXTRACT_DATA_OO RFC  
  
-   The Z_EXTRACT_DATA_OO RFC supports reading data from tables that satisfy the following conditions:  
  
    -   TabClass for the table is TRANSP, CUSTER, or POOL.  
  
    -   TabClass is VIEW and ViewClass is either D or P.  
  
-   Z_EXTRACT_DATA_OO does not support HR cluster tables, for example PCL1, PCL2, PCL3, PCL4, PCL5.  
  
-   The number of rows that can be extracted by Z_EXTRACT_DATA_OO depends on the hardware resources on the SAP server.  
  
-   All extracted data is returned in order of the primary keys.  
  
-   Tables or views containing the variable-length data types STRING, SSTRING and RAWSTRING are not supported. Tables or views containing these data types cannot be extracted.  
  
-   Z_EXTRACT_DATA_OO runs conversion exits on all fields that have conversion exits assigned to them. The resulting converted values must be entered in the WHERE clause of a SELECT statement. Converted values are also returned. This might cause inconsistencies between the results returned by Z_EXTRACT_DATA_OO and the results returned in the SAP data browser (SE16).  
  
-   Selected tables cannot contain field names that are reserved names in ABAP (for example, CONNECTION).  
  
-   Due to a limitation in the query processor in SAP R/3 version 4.6C, values for integer fields of type INT4 must be greater than or equal to -999999999 in the WHERE clause. Rows with INT4 values less than -999999999 will not be extracted regardless of whether the field containing the value is selected.  
  
-   Values for all data types in a WHERE clause are limited to 256 characters when executing on SAP system version 4.7 or greater; the limit is 70 characters in version 4.6c. For RAW data type values, these limits are halved to 128 and 35 characters, respectively. There is no limit on RAW and LCHR data type length when they are returned as a result.  
  
-   In SAP R/3 version 4.6C, fields in the WHERE clause are limited to 70 characters.  
  
-   In SAP R/3 version 4.6C, any table with a primary key field that has an output length greater than 70 characters cannot be extracted.  
  
-   In SAP R/3, version 4.6c, tables and views that contain variable length data types (`VARC`) are not supported, and tables and views containing these data types cannot be extracted from the data source using the Z_EXTRACT_DATA_OO function call.  
  
-   In file mode, the Z_EXTRACT_DATA_OO function call does not check whether a destination file is already opened, either by itself or by another application. Therefore, the function can incorrectly write to an open file while simultaneously appending data to the same file. No error is raised.  
  
-   In file mode, the Z_EXTRACT_DATA_OO function call can overwrite existing files. Ensure that SAP users who use Z_EXTRACT_DATA_OO have restricted file-system access by way of S_DATASET.  
  
## Security Considerations with the Custom RFC  
  
-   `Security Issue`: There is potential to expose data that is written to flat files if you do not help protect those files.  
  
     `Best practice`: Improve the security of the file share to which any data is written by the Z_EXTRACT_DATA_OO function call in flat file mode.  
  
-   `Security Issue`: There is the potential to overwrite files on any share that is written to using the Z_EXTRACT_DATA_OO function call in file mode. This can occur to any file on any share to which the SAP domain account has access.  
  
     `Best practice`: Strive to protect all shares to which the SAP domain account has access.  
  
-   `Security Issue`: Users have the ability to inspect (or "sniff") data during transmission from an SAP application server to its target file share, in cases when the target is on a different physical machine.  
  
     `Best practice`: Use IPsec or another appropriate method to help make communication more secure between the SAP server and its targets.  
  
## See Also  
 [About the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)