---
title: "Default OLE DB Data Types | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50070b5c-a3f1-4e6d-8ffa-842501d79b45
caps.latest.revision: 3
---
# Default OLE DB Data Types
The following table indicates the default OLE DB data types that result from the mapping of the host data types by the Microsoft OLE DB Provider for AS/400 and VSAM.  
  
|Host data type|OLE DB data type|Comments|  
|--------------------|----------------------|--------------|  
|Binary|DBTYPE_BYTES|A fixed-length array of bytes (unsigned char).|  
|Character|DBTYPE_STR|Null-terminated ASCII character string.|  
|Date|DBTYPE_DBDATE|The DBDATE typedef struct defined in OLEDB.H header file.|  
|DBCS|DBTYPE_STR|Null-terminated ASCII character string.|  
|DCBS – Mixed Either|DBTYPE_STR|Null-terminated ASCII character string.|  
|DCBS – Mixed Open|DBTYPE_STR|Null-terminated ASCII character string.|  
|DBCS – Variable|DBTYPE_STR|Null-terminated ASCII character string.|  
|DCBS – Variable Mixed Either|DBTYPE_STR|Null-terminated ASCII character string.|  
|DCBS – Variable Mixed Open|DBTYPE_STR|Null-terminated ASCII character string.|  
|Double|DBTYPE_R8|8-byte floating-point data.|  
|Float|DBTYPE_R8|8-byte floating-point data.|  
|Long Integer|DBTYPE_I4|4-byte signed integer.|  
|Long Variable Binary|DBTYPE_BYTES|A fixed-length array of bytes (unsigned char).|  
|Long Variable Character|DBTYPE_STR|Null-terminated ASCII character string.|  
|Packed|DBTYPE_DECIMAL|The DECIMAL structure typedef defined in OLEDB.H. This is an exact numeric value with a fixed precision and fixed scale.|  
|Real|DBTYPE_R4|4-byte floating-point data.|  
|Short|DBTYPE_I2|2-byte signed integer.|  
|Single|DBTYPE_R4|4-byte floating-point data.|  
|Time|DBTYPE_DBTIME|The DBTIME typedef defined in OLEDB.H header file.|  
|Time Stamp|DBTYPE_DBTIMESTAMP|The DBTIMESTAMP typedef defined in OLEDB.H header file.|  
|Variable Binary|DBTYPE_BYTES|A fixed-length array of bytes (unsigned char).|  
|Variable Character|DBTYPE_STR|Null-terminated ASCII character string.|  
|Zoned|DBTYPE_NUMERIC|The NUMERIC typedef structure defined in OLEDB.H. This is an exact numeric value with a fixed precision and fixed scale.|  
  
 The host Binary, VarBinary, and Long VarBinary data types are converted to SQL_C_CHAR type by the DDM DLL and mapped to the DBTYPE_BYTES data type by the SNAOLEDB DLL. The host Zoned data type is converted to SQL_C_CHAR type by the DDM DLL and mapped to the DBTYPE_NUMERIC data type by the SNAOLEDB DLL. The host Packed data type is converted to SQL_C_CHAR type by the DDM DLL and mapped to the DBTYPE_DECIMAL data type by the SNAOLEDB DLL.