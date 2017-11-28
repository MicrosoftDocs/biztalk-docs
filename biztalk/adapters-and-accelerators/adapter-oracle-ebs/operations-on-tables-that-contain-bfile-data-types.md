---
title: "Operations on Tables That Contain BFILE Data Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d7ebeb9-c2d6-4024-a169-263b947eeeb1
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on Tables That Contain BFILE Data Types
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] supports the BFILE data type in tables and stored procedures. 

## BFILE data types
The following table summarizes the BFILE data type exposed by the adapter based on the operation performed and the LOB artifact (table/procedure) accessed:  
  
|Artifact|Operation|Data type exposed for BFILE col/param|Comments|  
|--------------|---------------|--------------------------------------------|--------------|  
|TABLE|INSERT|String|Represents the logical Oracle directory path to the file to be inserted into the BFILE column<br /><br /> E.g. MYDIR/screen.jpg where MYDIR is a logical directory in Oracle|  
|TABLE|UPDATE|String|Represents the logical Oracle directory path to the file to be updated into the BFILE column|  
|TABLE|SELECT|byte[]|Represents the binary data constituting the BFILE|  
|STORED PROC|IN PARAM|String|Represents the logical Oracle directory path to the file to be inserted into the BFILE column<br /><br /> E.g. MYDIR/screen.jpg where MYDIR is a logical directory in Oracle|  
|STORED PROC|OUT PARAM|String|Represents the logical Oracle directory path to the file to be inserted into the BFILE column<br /><br /> E.g. MYDIR/screen.jpg where MYDIR is a logical directory in Oracle|  
|STORED PROC|INOUT PARAM|Not Supported|-|  
  
 The special operation `Read_<LOBColName>` is also supported on tables with BFILE data type, where \<LOBColName\> is the LOB column name in the table. The `Update_<LOBColName>` operation is not supported for BFILE data type. Adapter clients can alternately use the Update operation.  
  
## More good info  
  
-   The `Read_<LOBColName>` and `Update_<LOBColName>` operations, see [Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)