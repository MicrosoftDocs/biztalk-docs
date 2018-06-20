---
title: "Data Providers for DB21 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: beba8681-1b16-40a0-b4b7-5471c2c6876e
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Data Providers for DB2
## Platform Compatibility  
  
### Code Page Conversions  
 The Data Provider supports a combination of single byte character sets (SBCS), mixed-byte character sets (MBCS) double-byte character sets (DBCS), and Unicode - UTF8 [1208], which is an 8-bit Unicode transformation format.  
  
#### Host CCSID  
 The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. The default Host CCSID value is EBCDIC – U.S./Canada [37]. Typically, IBM DB2 database servers for z/OS and i5/OS utilize EBCDIC (Extended Binary Coded Decimal Interchange Code).  
  
#### PC Code Page  
 The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. The default PC code page is ANSI – Latin I [1252]. Typically, data consumers use either ANSI (American National Standards Institute) or Unicode.  
  
#### Process Binary as Character  
 The Data Providers for DB2 automatically converts to and from binary (CCSID 65535) and character string data types, based on the DB2 data type and Windows consumer data type. The DB2 encoding is determined by the Host CCSID. The Windows encoding is determined by the PC Code Page.  
  
### Data Type Mapping  
 This topic describes all data type mappings to OLE DB data types.  
  
#### DB2 to ADO.NET Data Type Mapping  
 The following table describes DB2 data type mappings to ADO.NET Provider for DB2 (MsDb2Client) data types (MsDb2Type).  
  
||||  
|-|-|-|  
|MsDb2Type|DB2 data type|Description|  
|BigInt|Bigint|A big integer is an 8-byte binary integer.|  
|Binary|Binary|A binary is a fixed-length binary string.|  
|Bit|Smallint|A small integer is a two-byte binary integer.|  
|BLOB|BLOB|A binary large object is a varying-length string used to store non-textual or binary data.|  
|Char|Char|A character is a fixed-length SBCS or MBCS string.|  
|CLOB|CLOB|A varying-length character large object is a varying-length string. The maximum length of the string depends on the DB2 platform and version.|  
|Date|Date|A date is a 10-byte string.|  
|DBCLOB|DCLOB|A varying-length double-byte character large object is a varying-length graphic double-byte only string. The maximum length of the string depends on the DB2 platform and version.|  
|Decimal|Decimal|A decimal is a packed decimal number.|  
|Double|Double|A double is an 8-byte double-precision floating point number.|  
|Graphic|Graphic|A graphic is a fixed-length DBCS only string.|  
|Int|Integer|An integer is a 4-byte binary integer.|  
|Numeric|Numeric|A numeric is a packed decimal number.|  
|Real|Real|A real is a 4-byte single-precision floating point number.|  
|SmallInt|Smallint|A small integer is a two-byte binary integer.|  
|Time|Time|A time is an 8-byte time string.|  
|Timestamp|Timestamp|A timestamp is a 26-byte string representing the date, time, and microseconds.|  
|TinyInt|Smallint|A small integer is a two-byte binary integer.|  
|VarBinary|Varbinary|A varying binary is a varying-length binary string.|  
|VarChar|Varchar|A varying character is a varying-length SBCS or MBCS character string.|  
|VarGraphic|Vargraphic|A varying graphic is a varying-length DBCS only string.|  
|VarWideChar|Vargraphic|A varying graphic is a varying-length Unicode only string.|  
|VarWideGraphic|Vargraphic|A varying graphic is a varying-length Unicode only string.|  
|WideChar|Graphic|A graphic is a fixed-length Unicode string.|  
|Xml|XML|A well-formed XML document string.|  
  
#### DB2 to OLE DB Data Type Mapping  
 The following table describes DB2 data type mappings to OLE DB data types.  
  
||||  
|-|-|-|  
|OLE DB data type|DB2 data type|Description|  
|DBTYPE_I8|Bigint|A big integer is an 8-byte binary integer.|  
|DBTYPE_Bytes|BINARY|A binary is a fixed-length binary string|  
|DBTYPE_Bytes|BLOB|A binary large object is a varying-length string used to store non-textual or binary data.|  
|DBTYPE_STR|Char|A character is a fixed-length SBCS or MBCS string.|  
|DBTYPE_WSTR|Char|A Unicode character is a fixed-length MBCS string.|  
|DBTYPE_STR|CLOB|A varying-length character large object is a varying-length string. The maximum length of the string depends on the DB2 platform and version.|  
|DBTYPE_DBDate|Date|A date is a 10-byte string.|  
|DBTYPE_Decimal|Decimal|A decimal is a packed decimal number.|  
|DBTYPE_R8|Double|A double is an 8-byte double-precision floating point number.|  
|DBTYPE_R8|Float|A float is an 8-byte double-precision floating point number.|  
|DBTYPE_WSTR|Graphic|A graphic is a fixed-length DBCS only string.|  
|DBTYPE_I4|Integer|An integer is a 4-byte binary integer.|  
|DBTYPE_STR|Long Varchar|A varying character is a varying-length SBCS or MBCS character string.|  
|DBTYPE_WSTR|Long Varchar|A varying varying-length Unicode string.|  
|DBTYPE_WSTR|Long Vargraphic|A varying graphic is a varying-length DBCS only string.|  
|DBTYPE_Numeric|Numeric|A numeric is a packed decimal number.|  
|DBTYPE_I2|Smallint|A small integer is a two-byte binary integer.|  
|DBTYPE_R4|Real|A real is a 4-byte single-precision floating point number.|  
|DBTYPE_DBTime|Time|A time is an 8-byte time string.|  
|DBTYPE_DBTimestamp|Timestamp|A timestamp is a 26-byte string representing the date, time, and microseconds.|  
|DBTYPE_Bytes|Varbinary|A varying binary is a varying-length binary string.|  
|DBTYPE_STR|Varchar|A varying character is a varying-length SBCS or MBCS character string.|  
|DBTYPE_WSTR|Varchar|A varying varying-length Unicode string.|  
|DBTYPE_WSTR|VarGraphic|A varying graphic is a varying-length DBCS only string.|  
  
 Schema information in OLE DB is retrieved using predefined schema rowsets with IDBSchemaRowset::GetRowset. The Data Provider exposed the PROVIDER_TYPES Rowset to indicate the DB2 to OLE DB data type support (types, mappings, limits), based on the IBM DB2 platform and version.  
  
#### DB2 for z/OS V9R1  
 The Data Provider supports accessing these data types when connected to DB2 for z/OS (based on V9R1).  
  
||||||  
|-|-|-|-|-|  
|DB2 Type_name|OLE DB data_type|Column_size|Minimum_scale|Maximum_scale|  
|Smallint|DBType_12|5|||  
|Integer|DBType_14|10|||  
|Bigint|DBType_18|19|||  
|Binary|DBType_Bytes|255|||  
|Real|DBType_R4|21|||  
|Float|DBType_R8|53|||  
|Double|DBType_R8|53|||  
|Decimal|DBType_Decimal|31|0|31|  
|Graphic|DBType_WSTR|127|||  
|VarGraphic|DBType_WSTR|16352|||  
|Char|DBType_STR|255|||  
|Varchar|DBType_STR|32672|||  
|Char|DBType_WSTR|255|||  
|Varchar|DBType_WSTR|32672|||  
|Numeric|DBType_Numeric|31|0|31|  
|Date|DBType_DBDate|10|||  
|Time|DBType_DBTime|8|||  
|Timestamp|DBType_Timestamp|26|||  
|BLOB|DBType_Bytes|2147483647|||  
|CLOB|DBType_STR|2147483647|||  
|Long Varchar|DBType_STR|32704|||  
|Long Varchar|DBType_WSTR|32704|||  
|Long Vargraphic|DBType_WSTR|16352|||  
|Varbinary|DBTypte_Bytes|32704|||  
  
#### DB2 for i5/OS V6R1  
 The Data Provider supports accessing these data types when connected to DB2 for i5/OS (based on V6R1).  
  
||||||  
|-|-|-|-|-|  
|DB2 Type_name|OLE DB data_type|Column_size|Minimum_scale|Maximum_scale|  
|Binary|DBType_Bytes|32765|||  
|Smallint|DBType_12|5|||  
|Integer|DBType_14|10|||  
|Bigint|DBType_18|19|||  
|Real|DBType_R4|24|||  
|Float|DBType_R8|53|||  
|Double|DBType_R8|53|||  
|Decimal|DBType_Decimal|63|0|31|  
|Graphic|DBType_WSTR|16382|||  
|VarGraphic|DBType_WSTR|16369|||  
|Char|DBType_STR|32765|||  
|Varchar|DBType_STR|32739|||  
|Char|DBType_WSTR|32765|||  
|Varchar|DBType_WSTR|32739|||  
|Numeric|DBType_Numeric|31|0|31|  
|Date|DBType_DBDate|10|||  
|Time|DBType_DBTime|8|||  
|Timestamp|DBType_Timestamp|26|||  
|BLOB|DBType_Bytes|2147483647|||  
|CLOB|DBType_STR|2147483647|||  
|Varbinary|DBType_Bytes|32739|||  
  
#### DB2 for LUW V9.7  
 The Data Provider supports accessing these data types when connected to DB2 for LUW (based on V9.7).  
  
||||||  
|-|-|-|-|-|  
|DB2 Type_name|OLE DB data_type|Column_size|Minimum_scale|Maximum_scale|  
|Binary|DBType_Bytes|254|||  
|Smallint|DBType_12|5|||  
|Integer|DBType_14|10|||  
|Bigint|DBType_18|19|||  
|Real|DBType_R4|24|||  
|Float|DBType_R8|53|||  
|Double|DBType_R8|53|||  
|Decimal|DBType_Decimal|31|0|31|  
|Graphic|DBType_WSTR|127|||  
|VarGraphic|DBType_WSTR|16336|||  
|Char|DBType_STR|254|||  
|Varchar|DBType_STR|4000|||  
|Char|DBType_WSTR|254|||  
|Varchar|DBType_WSTR|4000|||  
|Char() for BIT data|DBType_Bytes|254|||  
|Varchar() for BIT data|DBType_Bytes|32672|||  
|Numeric|DBType_Numeric|31|0|31|  
|Date|DBType_DBDate|10|||  
|Time|DBType_DBTime|8|||  
|Timestamp|DBType_Timestamp|26|||  
|BLOB|DBType_Bytes|2147483647|||  
|CLOB|DBType_STR|2147483647|||  
|Long Varchar|DBType_STR|32700|||  
|Long Varchar|DBType_STR|32700|||  
|Long Varchar|DBType_WSTR|16350|||  
|Varbinary|DBTYPE_BYTES|32762|||  
  
#### SQL Server Integration Services  
 When using the SQL Server Integration Services Import and Export Wizards from the Microsoft SQL Server Management Studio, you can customize the default data conversions by editing the XML mapping files. The XML files are located at ate C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles.  
  
#### SQL Server Replication Services  
 SQL Server Replication may convert data incorrectly, based on the default mappings from SQL Server to DB2 data types. We recommend that the administrator and developer review and revise the Replication data type mappings using the following SQL Server system stored procedures.  
  
- ·sp_helpdatatypemap  
  
- ·sp_getdefaultdatatypemapping  
  
- ·sp_setdefaultdatatypemapping  
  
  For more information, see the [System Stored Procedures (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=180765) (http://go.microsoft.com/fwlink/?LinkID=180765) topic in SQL Server Books Online.