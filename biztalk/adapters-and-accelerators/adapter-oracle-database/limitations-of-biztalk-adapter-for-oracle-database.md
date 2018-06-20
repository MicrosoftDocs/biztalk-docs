---
title: "Limitations of BizTalk Adapter for Oracle Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapter, limitations of"
ms.assetid: eab4ddea-f986-43c2-82bb-b9fe37961a5b
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Limitations of BizTalk Adapter for Oracle Database
## General  
 The following are known limitations for the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:  
  
- Barring some exceptions, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is compatible with the previous release of the adapters. For a list of changes that has happened since the last release, see [Key Features in BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md).  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support XML Types.  
  
- The SQLEXECUTE operation does not return values for OUT or IN OUT parameters to procedures, functions, or packages. For this reason, you must invoke procedures, functions, and packages by using the dedicated operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes for these Oracle artifacts.  
  
- When retrieving data from the Oracle database using proxy programming, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not deserialize XML messages that have more than 65536 nodes. Make sure the response message has nodes less than or equal to 65536. You can work around this limitation by modifying the app.config file for your application. For instructions, see [Troubleshoot operational issues with the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-operational-issues-with-the-oracle-database-adapter.md).  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] takes input strings and constructs SQL commands that are then executed by the adapter. However, the input string might contain other SQL commands that also get executed and might break the operation contract.  
  
   Consider a scenario where the adapter provides an input REF CURSOR to a stored procedure. In such a scenario, the adapter client must provide a command that, when executed, obtains the REF CURSOR. The adapter then passes on the REF CURSOR to the stored procedure. However, if the command for obtaining the REF CURSOR performs some additional modifications to the database, the operation contract for executing the stored procedure is broken.  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports UDT nesting only up to two levels.  
  
- When using the adapters with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], if the credentials on the WCF-custom send port are incorrect, the request messages are not processed. After you specify the correct credentials, the message is sent to the Oracle database and a response is received. However, the response message is not available to the out port. In such scenarios, you may need to restart the host instance.  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support the BFILE data type inside complex types (such as RECORD type, TABLE type, UDT, and VARRAY).  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support User-Defined Types (UDTs) that have circular references.  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support records that contain fields of type PL/SQL tables of RECORD type.  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not enable clients to set the value of the first element in a VARRAY to NULL.  
  
- Except for PL/SQL tables, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support UDTs that are defined inside a package.  
  
## Limitations due to ODP.NET  
 The following are known limitations for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] due to the limitation of ODP.NET:  
  
- For Oracle data types that take decimal values, ODP.NET does not throw an exception if the input value contains alphabetic characters. Because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses ODP.NET to interface with the Oracle database, the adapter too does not throw an exception when passing alphabetic characters. For example:  
  
  -   Passing a value “54r” for an insert operation does not throw an exception; the value “54” is inserted instead.  
  
  -   Passing a value “r54” for an insert operation does not throw an exception; the value “0” is inserted instead.  
  
- Because of an ODP.NET limitation, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support the use of overloaded procedures using strongly-typed and weakly-typed REF CURSORS. Internally, the adapter treats both the strongly-typed and weakly-typed REF CURSORS as just REF CURSORS.  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support PL/SQL tables that are not indexed by a numeric field.  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support associative arrays that do not contain any element.  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support UDTs that contain the TimeStamp data type with local time zone attributes (TimeStampLTZ).  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support UDTs that contain a “.” (period) in their names.  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support UDTs that contain BLOB, CLOB, and NCLOB data types as an IN OUT parameter.  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support Varray of Varray of the following simple types: BFILE, IntervalDS, IntervalYM, TimeStampLTZ, and TimeStampTZ.  
  
- Due to the limitation of associative arrays, PL/SQL tables or PL/SQL tables of records that contain any of the following data types are not supported in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:  
  
  -   BFILE  
  
  -   BLOB  
  
  -   CLOB  
  
  -   IntervalDS  
  
  -   IntervalYM  
  
  -   Long  
  
  -   NCLOB  
  
  -   RowID  
  
  -   TimeStamp  
  
  -   TimeStampLTZ  
  
  -   TimeStampTZ  
  
## See Also  
 [Understand the BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)