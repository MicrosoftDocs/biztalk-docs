---
title: "Operations on tables and views that contain LOB data in Oracle Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data type"
  - "binary file"
  - "UpdateLOB"
  - "ReadLOB"
  - "LOB data types"
  - "NCLOB"
  - "large object"
  - "binary large object"
  - "CLOB"
  - "national character large object"
  - "BFILE"
  - "BLOB"
  - "character large object"
ms.assetid: 25afd8c7-8ca3-4855-a231-2bec28c9a5cb
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on tables and views that contain LOB data in Oracle Database
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] provides support for the Oracle large object (LOB) data types:  
  
- Binary large object (BLOB)  
  
- Character large object (CLOB)  
  
- National character large object (NCLOB)  
  
- Binary file (BFILE). For more information, see [Operations on Tables that contains BFILE Data Types](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md).  
  
  On the Oracle database, LOB data types are used to store large amounts of data (up to 4 GB). LOB types support both input and output streaming.  
  
  The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces the following operations for tables and views that contain LOB columns:  
  
- **ReadLOB**. The ReadLOB operation is surfaced for tables and views that contain BLOB, CLOB, NCLOB, and BFILE columns. By using the ReadLOB operation, adapter clients can read values in a LOB column as a data stream. This operation takes the LOB data type column name and a filter string as parameters. Adapter clients must ensure that the filter string fetches exactly one matching row. If there is more than one matching row, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] only returns the LOB column for the first (matching) row.  
  
  > [!NOTE]
  >  The ReadLOB operation is designed to support input streaming of LOB data in the WCF service model. You should use a table Select operation to read LOB data from a WCF Channel Model or [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution. For more information about streaming, see [Streaming Support for LOB Data Types in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md).  
  
- **UpdateLOB**. The UpdateLOB operation is surfaced for tables and views that contain BLOB, CLOB, and NCLOB columns. By using the UpdateLOB operation, adapter clients can update values in a LOB column. This operation takes the LOB data type column name, a filter string, and base64binary encoded data as parameters. Adapter clients must ensure that the filter string fetches exactly one matching row; otherwise the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] throws an XmlReaderParsingException.  
  
  > [!NOTE]
  >  The UpdateLOB operation:  
  > 
  > - Is not supported for the BFILE data type. Adapter clients can alternatively use the Update operation. For more information, see [Operations on Tables that contains BFILE Data Types](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md).  
  >   -   Must be performed as part of a transaction. To ensure this, the **UseAmbientTransaction** binding property must be set to **True**. For information about the **UseAmbientTransaction** binding property, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
> [!NOTE]
>  ReadLOB and UpdateLOB operate on a single LOB column in a single table row. To operate on LOB columns in multiple rows or on multiple LOB columns within a single row, you must invoke ReadLOB or UpdateLOB for each target column within each target row.  
  
 For more information about:  
  
- Invoking the UpdateLOB operation on an Oracle database table using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Performing Operations on Tables with Large Object Types Data by Using BizTalk Server](https://msdn.microsoft.com/library/cc185405(v=bts.10).aspx). (You should use a table Select operation to read LOB data types in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].)  
  
- Invoking ReadLOB and UpdateLOB operations on an Oracle database table using WCF service model, see [Run Operations on Tables with Large Object Types by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md).  
  
- Message structure and SOAP actions for performing ReadLOB and UpdateLOB operations, see [Message Schemas for Special LOB Operations](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185259(v=bts.10).aspx)