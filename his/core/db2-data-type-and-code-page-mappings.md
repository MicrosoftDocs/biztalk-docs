---
title: "DB2 Data Type and Code Page Mappings | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cca7e3a6-6160-48ca-89d2-90318900807f
caps.latest.revision: 2
---
# DB2 Data Type and Code Page Mappings
This topic contains information that describes DB2 data type mappings in the Microsoft OLE DB provider for DB2 (Data Provider).  
  
## Code Page Conversions  
 The Data Provider supports a combination of single byte character sets (SBCS), mixed-byte character sets (MBCS) double-byte character sets (DBCS), and Unicode - UTF8 [1208], which is an 8-bit Unicode transformation format. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
##  <a name="h1-5"></a> Data Type Mappings  
 The following table describes DB2 data type mappings to OLE DB data types.  
  
|||  
|-|-|  
|**DB2 data type**|**Description**|  
|BIGINT|An 8-byte integer. This data type is converted to DBTYPE_I8 for use by OLE DB.|  
|CHAR() FOR BIT DATA|A fixed binary length string containing character data. The maximum length of the string depends on the DB2 platform and version. This data type is converted to a DBTYPE_BSTR BYTES for use by OLE DB.|  
|CHAR|A fixed-length SBCS or MBCS string. The maximum length of the string depends on the DB2 platform and version. This data type is converted to a DBTYPE_STR for use by OLE DB.|  
|CHAR|A fixed-length mixed Unicode string. The maximum length of the string depends on the DB2 platform and version. This data type is converted to a DBTYPE_WSTR for use by OLE DB.|  
|DATE|A 10-byte date string. This data type is converted to a DBTYPE_DBDATE for use by OLE DB.|  
|DECIMAL|A packed decimal number. This data type is converted to a DBTYPE_DECIMAL for use by OLE DB.|  
|DOUBLE|An 8-byte double-precision floating point number. This data type is converted to a DBTYPE_R8 for use by OLE DB.|  
|FLOAT|An 8-byte double-precision floating point number. This data type is the same as a DOUBLE. This data type is converted to a DBTYPE_R8 for use by OLE DB.|  
|GRAPHIC|A fixed-length DBCS only string. The maximum length of the string depends on the DB2 platform and version. This data type is converted to a DBTYPE_WSTR for use by OLE DB.|  
|INTEGER|A 4-byte integer ranging in value from -2,147,463,648 to +2,147,483,647. This data type is converted to a DBTYPE_I4 for use by OLE DB.|  
|NUMERIC|A packed decimal number. This data type is converted to a DBTYPE_NUMERIC for use by OLE DB.|  
|SMALLINT|A SMALLINT (small integer) is a two-byte integer with a precision of 5 digits ranging from -32,768 to +32,767. This data type is converted to a DBTYPE_I2 for use by OLE DB.|  
|REAL|A 4-byte single-precision floating point number. This data type is converted to a DBTYPE_R4 for use by OLE DB.|  
|TIME|An 8-byte time string. This data type is converted to a DBTYPE_DBTIME for use by OLE DB.|  
|TIMESTAMP|A 26-byte string representing the date, time, and microseconds. This data type is converted to a DBTYPE_DBTIMESTAMP for use by OLE DB.|  
|VARCHAR() FOR BIT DATA|A varying-length binary  string containing character data. The maximum length of the string depends on the DB2 platform and version. This data type is converted to a DBTYPE_BYTES for use by OLE DB.|  
|VARCHAR|A varying-length SBCS or MBCS character string. The maximum length of the string depends on the DB2 platform and version. This data type is converted to a DBTYPE_STR for use by OLE DB.|  
|VARCHAR|A varying-length Unicode string. The maximum length of the string depends on the DB2 platform and version. This data type is converted to a DBTYPE_WSTR for use by OLE DB.|  
|VARGRAPHIC|A varying-length DBCS only string. The maximum length of the string depends on the DB2 platform and version. This data type is converted to a DBTYPE_WSTR for use by OLE DB.|  
  
## See Also  
 [OLE DB Provider for DB2 Programmer's Guide](../core/ole-db-provider-for-db2-programmer-s-guide.md)