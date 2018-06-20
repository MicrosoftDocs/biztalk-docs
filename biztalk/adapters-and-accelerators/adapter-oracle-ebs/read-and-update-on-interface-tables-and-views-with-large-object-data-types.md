---
title: "Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f6e8db6-ba68-4e3f-84b2-1cc31ce89bcb
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] provides support for the Oracle large object (LOB) data types:  
  
- Binary large object (BLOB)  
  
- Character large object (CLOB)  
  
- National character large object (NCLOB)  
  
- Binary file (BFILE). For more information, see [Operations on Tables That Contain BFILE Data Types](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md).  
  
  In the underlying Oracle database, LOB data types are used to store large amounts of data, up to 4 gigabytes (GB). Except for the BFILE data type, LOB data types support both input and output streaming.  

## Operations for tables and views  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] surfaces the following operations for interface tables, interface views, tables and views that contain LOB columns:  
  
- **Read_\<LOBColName\>**: The `Read_<LOBColName>` operation is surfaced for interface tables, interface views, tables and views that contain BLOB, CLOB, NCLOB, and BFILE columns, where \<LOBColName\> is the name of the column of type BLOB, CLOB, NCLOB or BFILE. By using the Read_\<LOBColName\> operation, adapter clients can read values in an LOB column as a data stream. This operation takes a filter string as parameter.  
  
  > [!NOTE]
  >  The `Read_<LOBColName>` operation is designed to support input streaming of LOB data in the WCF service model. You should use a table Select operation to read LOB data from a WCF channel model or [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
- **Update_\<LOBColName\>**: The `Update_<LOBColName>` operation is surfaced for interface tables and tables only that contain BLOB, CLOB, and NCLOB columns, where \<LOBColName\> is the name of the column of type BLOB, CLOB, and NCLOB. By using the Update_\<LOBColName\> operation, adapter clients can update values in an LOB column. For the BLOB data type, this operation takes base64binary encoded data as the parameter, whereas for the CLOB and NCLOB data types, this operation takes a string filter as the parameter.  
  
  > [!NOTE]
  >  The `Update_<LOBColName>` operation:  
  > 
  > - Is not supported for the BFILE data type. Adapter clients can alternatively use the Update operation. For more information, see [Operations on Tables That Contain BFILE Data Types](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md).  
  >   -   Is not exposed for interface views and views.  
  >   -   Must be performed as part of a transaction. To ensure this, the **UseAmbientTransaction** binding property must be set to **True**. For information about the **UseAmbientTransaction** binding property, see [Rad about the  BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
> [!IMPORTANT]
>  The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] surfaces a `Read_<LOBColName>` and an `Update_<LOBColName>` operation for each LOB column in a table. So, if there are two LOB columns in a table (LOBCol1 and LOBCol2), you have two `Read_<LOBColName>` operations (Read_LOBCol1 and Read_LOBCol2) and two `Update_<LOBColName>` operations (Update_LOBCol1 and Update_LOBCol2).  
  
## More good info  
  
- Invoking the `Read_<LOBColName>` and `Update_<LOBColName>` operations on a table in the underlying database in Oracle E-Business Suite using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run Operations on Tables with Large Data Types Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter.md).  
  
- Message structure and SOAP actions for performing `Read_<LOBColName>` and `Update_<LOBColName>` operations, see [Message Schemas for Special LOB Operations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-special-lob-operations1.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)