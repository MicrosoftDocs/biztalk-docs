---
title: "Data Conversion | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e05cbca-bde4-45e7-962f-ae9e62e37598
caps.latest.revision: 6
---
# Data Conversion
The design of the OLE DB APIs is similar to the APIs provided by ODBC and other ISAM APIs. The APIs are handle-based. After opening a file, the application can determine the buffer size required to store a row, use the cursor APIs to move, and optionally retrieve one or more rows of data using the row-level binding.  
  
 Data is converted to default C data types as defined in ODBC, as illustrated in the following table.  
  
|Host data type|Default C data type|  
|--------------------|-------------------------|  
|Binary|unsigned char binary[]|  
|Character|char string[]|  
|Date (in character format)|date struct|  
|Double|Double|  
|Long|Int|  
|Packed|unsigned char number[]|  
|Short|Short|  
|Single|Float|  
|Time (in character format)|time struct|  
|Time Stamp (in character format)|timestamp struct|  
|Variable Binary|unsigned char binary[]|  
|Variable Character|char string[]|  
|Zoned|unsigned char number[]|  
  
 Data conversions from a large numeric type to a small numeric type are supported (from DOUBLE to SINGLE and from INT to SMALLINT, for example). However, truncation and conversion errors can occur that will not be reported by the OLE DB Provider for AS/400 and VSAM.  
  
 The OLE DB Provider for AS/400 and VSAM has a number of other limitations:  
  
-   Positive signed floating-point values cannot be read from ZONED DECIMAL fields.  
  
-   No floating point values can be inserted into ZONED DECIMAL fields.  
  
-   No values can be inserted into single-precision FLOATING POINT fields.  
  
-   Positive signed floating-point values cannot be inserted into PACKED DECIMAL fields.  
  
-   The ADO **Find** method fails to locate the first record when the key is multiple columns and the first column is a VARCHAR or TIME data type.