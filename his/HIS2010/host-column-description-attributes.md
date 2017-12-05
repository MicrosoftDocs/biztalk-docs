---
title: "Host Column Description Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 931be354-c203-490a-9c82-243e1405161c
caps.latest.revision: 4
---
# Host Column Description Attributes
Attributes are shown in the following table.  
  
|Attribute|Field number|Description|  
|---------------|------------------|-----------------|  
|Reserved|1|Always zero|  
|Column Name|2|Character string|  
|Alias|3|Character string|  
|Precision|4|Numeric value|  
|Scale|5|Numeric value|  
|Length|6|Numeric value|  
|Host Type|7|Keyword representing the host data type|  
|OLE DB Type|8|Keyword representing the local OLE DB data type|  
|Nullable|9|Y or N|  
|CCSID|10|Numeric value|  
|Title|11|Character string|  
  
 **Column Name**  
 The Column Name attribute is the character string that represents the name of the column. This attribute may be null.  
  
 **Alias**  
 The Alias attribute is an optional character string that represents an alias label for the column string name. This attribute may be null.  
  
 **Precision**  
 The Precision attribute is the total number of decimal digits in the column containing numeric data on the host. The only two fixed-point numeric data types that require this information are the NUMERIC and DECIMAL keyword data types, and for these types this field cannot be null and must contain a valid numeric value.  
  
 The precision must be set the same as the length attribute for CHAR and BINARY keyword data types, and set to zero for the other types. Precision has no default value and must not be left null.  
  
 **Scale**  
 The Scale attribute is the number of decimal digits to the right of any decimal point for numeric data on the host. The only two numeric data types that require this information are the NUMERIC and DECIMAL keyword data types, and for these types this field cannot be null and must contain a valid numeric value. For other numeric (the SINGLE and DOUBLE keywords, for example) and nonnumeric data types (binary, character, date, time, and timestamp), the scale should be set to zero. This field must not be left null and must contain a numeric value.  
  
 **Length**  
 The Length attribute is the total length of the data on the host. This field must not be left empty and must contain a numeric value.  
  
 **Host Type**  
 The Host Type attribute is a keyword value that represents the data type of the host data. This keyword value is based on standard data types used on AS/400 and VSAM files. If no keyword is entered, this attribute defaults to the BINARY keyword. The following table describes the allowable types for AS/400 and VSAM.  
  
|Host type name|Keyword|Comment|  
|--------------------|-------------|-------------|  
|Binary|BINARY|Fixed-length binary data (no character code conversions). The length must be specified.|  
|Character|CHAR|Fixed-length character data. The length must be specified.|  
|Date|DATE|The date represented as character data in the format yyyy-mm-dd that fits in 10 bytes.|  
|DBCS|DBCS|Fixed-length character data that can contain only DBCS data.|  
|DCBS – Mixed Either|MIXED_EITHER|Fixed-length character data that can contain either DBCS or alphanumeric data.|  
|DCBS – Mixed Open|MIXED_OPEN|Fixed-length character data that can contain both DBCS and alphanumeric data. DBCS data is distinguished from alphanumeric data with SHIFT+CTRL characters.|  
|DBCS – Variable|VARDBCS|Variable-length character data with a prefix of 2 bytes for length that contains only DBCS data. The maximum possible length for the column containing this data type must be specified.|  
|DCBS – Variable Mixed Either|VARMIXED_EITHER|Variable-length character data with a prefix of 2 bytes for length that can contain either DBCS or alphanumeric data. The maximum possible length for the column containing this data type must be specified.|  
|DCBS – Variable Mixed Open|VARMIXED_OPEN|Variable-length character data with a prefix of 2 bytes for length that can contain both DBCS and alphanumeric data. DBCS data is distinguished from alphanumeric data with SHIFT+CTRL characters. The maximum possible length for the column containing this data type must be specified.|  
|Double|DOUBLE|Floating-point data that fits in 8 bytes (64 bits).|  
|Long|LONG|Integer data that fits in 4 bytes (32 bits).|  
|Long Variable Binary|LONGVARBINARY|Variable-length binary data represented as an unsigned character array with prefix 2 bytes for length. The maximum possible length for the column containing this data type must be specified.|  
|Long Variable Character|LONGVARCHAR|Variable-length character data with a prefix of 2 bytes for the length. The maximum possible length for the column containing this data type must be specified.|  
|Packed|PACKED|Packed decimal numeric data where the precision and scale are exactly as specified.|  
|Short|SHORT|Integer data that fits in 2 bytes (16 bits).|  
|Single|SINGLE|Floating-point data that fits in 4 bytes (32 bits).|  
|Time|TIME|The time represented as character data in the format hh:mm:ss that fits in 8 bytes.|  
|Time Stamp|TIMESTAMP|Timestamp represented as characters in the format yyyy-mm-dd hh:mm:ss.ffffff that fits in 19 bytes.|  
|Variable Binary|VARBINARY|Variable-length binary data represented as an unsigned character array with prefix 2 bytes for length. The maximum possible length for the column containing this data type must be specified.|  
|Variable Character|VARCHAR|Variable-length character data with a prefix of 2 bytes for length. The maximum possible length for the column containing this data type must be specified.|  
|Zoned|ZONED|Zoned decimal numeric data where the precision and scale are exactly as specified.|  
  
 Note that the OLE DB provider limits the maximum length character field that can be accessed on an AS/400 computer to 32,745. Attempting to access a character field greater than this length on an AS/400 computer can have unpredictable results and can cause the OLE DB provider to stop responding.  
  
 Note that the floating-point data format assumed by the OLE DB Provider for AS/400 and VSAM depends on the host. For AS/400, the host floating-point data format is assumed to be IEEE. On mainframe hosts, floating-point data types are assumed to be in IBM floating-point formats. Because OLE DB supports the IEEE floating-point format, data conversion errors can occur when converting the extreme values of VSAM floating-point data in IBM format to IEEE floating-point data by the OLE DB provider.  
  
 Note that the DECIMAL, FLOAT, INTEGER, NUMERIC, REAL, and SMALLINT keywords should not be used in HCD files and should be replaced with the newer keywords as follows:  
  
-   The DOUBLE keyword replaces the FLOAT keyword.  
  
-   The LONG keyword replaces the INTEGER keyword.  
  
-   The PACKED keyword replaces the NUMERIC keyword.  
  
-   The SHORT keyword replaces the SMALLINT keyword.  
  
-   The SINGLE replaces the REAL keyword.  
  
-   The ZONED keyword replaces the DECIMAL keyword.  
  
 The Data Descriptions management console snap-in provided with Host Integration Server does not work properly with HCD files containing these older keywords and will give unpredictable results.  
  
 **OLE DB Type**  
 The OLE DB Type attribute is a keyword that represents the data type of the local personal computer data. This keyword value is based on the standard OLE DB data types as defined in the OLEDB.H header file included with the OLE DB SDK version 1.5 and later. The data structures for the date, time, and timestamp C data types are defined as typedefs in the OLEDB.H header file included with the OLE DB SDK. If no keyword is entered, this attribute defaults to the BINARY keyword.  
  
 For the decimal and numeric host data types, the OLE DB Type attribute must be set to DBTYPE_STR. These two fixed-point numeric types are currently converted to character data strings by the DDM layer of the Microsoft OLE DB Provider for AS/400 and VSAM. If these host types are converted to any of the defined OLE DB numeric C types, numeric accuracy can be lost.  
  
 The allowable types are listed in the following table.  
  
|OLE DB type name|Keyword|Comment|  
|----------------------|-------------|-------------|  
|DBTYPE_BYTES|BINARY|Fixed-length binary data represented as an unsigned char array.|  
|DBTYPE_DBDATE|DATE|The OLE DB DBDATE typedef struct as defined in the OLEDB.H header file.|  
|DBTYPE_DBTIME|TIME|The OLE DB DBTIME typedef as defined in the OLEDB.H header file.|  
|DBTYPE_DBTIMESTAMP|TIMESTAMP|The OLE DB DBTIMESTAMP typedef struct as defined in the OLEDB.H header file.|  
|DBTYPE_DECIMAL|DECIMAL|The OLE DB DECIMAL typedef struct as defined in the OLEDB.H header file.|  
|DBTYPE_I2|SHORT|Integer data stored in 2 bytes (16 bits).|  
|DBTYPE_I4|LONG|Integer data stored in 4 bytes (32 bits).|  
|DBTYPE_NUMERIC|NUMERIC|The OLE DB NUMERIC typedef struct as defined in the OLEDB.H header file.|  
|DBTYPE_R4|FLOAT|Floating-point data stored in 4 bytes (32 bits).|  
|DBTYPE_R8|DOUBLE|Floating-point data stored in 8 bytes (64 bits).|  
|DBTYPE_STR|CHAR|Character data.|  
|DBTYPE_I1|Not applicable|Not supported (signed tiny integer stored in one byte, 8 bits).|  
|DBTYPE_I8|Not applicable|Not supported (signed long integer stored in eight bytes, 64 bits).|  
|DBTYPE_UI1|Not applicable|Not supported (unsigned tiny integer stored in one byte, 8 bits).|  
|DBTYPE_UI2|Not applicable|Not supported (unsigned short integer stored in two bytes, 16 bits).|  
|DBTYPE_UI4|Not applicable|Not supported (unsigned long integer stored in four bytes, 32 bits).|  
|DBTYPE_UI8|Not applicable|Not supported (unsigned long integer stored in eight bytes, 64 bits).|  
  
 **Nullable**  
 The Nullable attribute indicates whether this field can be a null value. Legal values for this field are Y or N. If this field is empty, the default value for nullable is N. The current version of the OLE DB Provider for AS/400 and VSAM does support nullable fields, so this value must be set to N.  
  
 **CCSID**  
 The character code set identifier (CCSID) attribute indicates the character set used on the host. If this field is empty, the default value for CCSID is set to EBCDIC US English (37). The CCSID setting used by the OLE DB provider must be set to match the CCSID actually used on the host, otherwise data loss will occur. Note that some AS/400 systems default to a CCSID of 937, rather than 37, for enabling double-byte character sets (DBCS).  
  
 If the CCSID is set to 0 or 65535, no character translation will take place when converting character data from the host to the personal computer by the OLE DB provider. The allowable values for CCSID when used with OLE DB Provider for AS/400 and VSAM are listed in the following table.  
  
|EBCDIC character set|CCSID value|  
|--------------------------|-----------------|  
|U.S./Canada|37|  
|Germany|273|  
|Denmark/Norway|277|  
|Finland/Sweden|278|  
|Italy|280|  
|Latin America/Spain|284|  
|United Kingdom|285|  
|France|297|  
|International|500|  
  
 Note that this value needs to correspond to the CCSID used on the host.  
  
 **Title**  
 The Title attribute is an optional character string that represents a comment describing the column. This attribute may be null.