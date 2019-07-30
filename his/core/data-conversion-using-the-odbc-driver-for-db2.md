---
title: "Data Conversion using DB2 ODBC Driver | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9148450a-f72f-45ed-8041-08318bf781ef
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Data Conversion Using the ODBC Driver for DB2
The design of ODBC APIs is similar to other ISAM APIs. The APIs are handle-based. After opening a file, the application can determine the buffer size required to store a row, use the cursor APIs to move, and optionally retrieve one or more rows of data using the row-level binding.  
  
 Data is converted to default SQL data types, as defined in ODBC. The following table lists these conversions.  
  
|DB2 data type|Default SQL Data Type|Exposed as Native Type in SQLGetTypeInfo|Comments|  
|-------------------|---------------------------|----------------------------------------------|--------------|  
|**BIGINT**|||An 8-byte integer.<br /><br /> This data type is supported on DB2 UDB only.|  
|**BLOB**|||A Binary Large Object (BLOB) is a varying-length string that can be up to 2 gigabytes in length. A BLOB is primarily intended to hold binary data.<br /><br /> This data type is not supported by the ODBC Driver for DB2.|  
|**CHAR** (BIT)|SQL_BINARY|No|A fixed length (double-byte only) character string.|  
|**CHAR** (SBCS)|SQL_CHAR|Yes|A fixed-length SBCS character string.|  
|**CHAR** (MIXED)|SQL_CHAR|No|A fixed-length mixed (single and double-byte) character string.|  
|**CLOB**|||A Character Large Object(CLOB) is a varying-length string that can be up to 2 gigabytes in length. A CLOB is used to store large single-byte character set data. A CLOB is considered to be a character string.<br /><br /> This data type is not supported by the ODBC Driver for DB2.|  
|**DATE**|SQL_TYPE_DATE|Yes|A 10-byte date string.<br /><br /> This data type is converted to an SQL_DATE for use by ODBC.|  
|**DBCLOB**|||A Double-Byte Character Large Object (DBCLOB) is a varying-length string of double-byte characters that can be up to 2 gigabytes in length (1,073,741,823 double-byte characters). A DBCLOB is used to store large double-byte character set data. A DBCLOB is considered to be a graphic string.<br /><br /> It is not supported by the ODBC Driver for DB2.|  
|**DECIMAL**|SQL_DECIMAL|Yes|A packed decimal number.|  
|**DOUBLE**|SQL_DOUBLE|Yes|An 8-byte double-precision floating point number.|  
|**FLOAT**|SQL_FLOAT|Yes|An 8-byte double-precision floating point number. This data type is the same as a DOUBLE.|  
|**GRAPHIC** (DBCS)|SQL_CHAR|No|A fixed-length graphic string consisting of a sequence of double byte (DBCS only) character string data.|  
|**INTEGER**|SQL_INTEGER|Yes|A 4-byte integer with a precision of 10 digits ranging in value from  -2,147,463,648 to +2,147,483,647.|  
|**LONG VARCHAR** (BIT)|SQL_BINARY|No|A varying-length (double-byte only) character string.|  
|**LONG VARCHAR** (SBCS)|SQL_CHAR|No|A varying-length SBCS character string.|  
|**LONG VARCHAR** (MIXED)|SQL_CHAR|No|A varying-length mixed-character (single and double-byte) string.|  
|**LONG VARGRAPHIC** (DBCS)|SQL_LONGVARCHAR|No|A varying-length graphic string consisting of a sequence of double byte (DBCS only) character string  data.|  
|**SMALLINT**|SQL_SMALLINT|Yes|A SMALLINT (small integer) is a two-byte integer with a precision of 5 digits ranging from -32,768 to +32,767.|  
|**REAL**|SQL_REAL|Yes|A 4-byte single-precision floating point number.|  
|**TIME**|SQL_TYPE_TIME|Yes|An 8-byte time string.<br /><br /> When using ActiveX Data Objects to return data from a DB2 TIME data type, ADO returns a DATETIME value.|  
|**TIMESTAMP**|SQL_TYPE_TIMESTAMP|Yes|A 26-byte string representing the date, time, and microseconds.|  
|**VARCHAR** (BIT)|SQL_BINARY|No|A varying-length (double-byte only) character string.|  
|**VARCHAR** (SBCS)|SQL_CHAR|Yes|A varying-length character string.|  
|**VARCHAR** (MIXED)|SQL_CHAR|No|A varying-length mixed (single and double-bye) character string.|  
|**VARGRAPHIC** (DBCS)|SQL_VARCHAR|No|A varying-length graphic string consisting of a sequence of double byte (DBCS only) character string data.|  
  
 Not all platforms and versions of DB2 support all of the above-referenced data types. Consult your IBM SQL Reference for the specific target and platform and version of DB2.  
  
 The ODBC Driver for DB2 exposes only selected DB2 data types as native types in the ODBC catalog function **GetTypeInfo**. For example, the driver does not expose LONG CHARACTER or VARYING LONG CHARACTER types. Rather these types are exposed as CHARACTER and VARYING CHARACTER respectively. Also, the driver exposes CHARACTER FOR SBCS DATA, CHARACTER FOR MIXED DATA, and CHARACTER FOR BIT DATA as CHARACTER. The driver exposes VARYING CHARACTER FOR SBCS DATA, VARYING CHARACTER FOR MIXED DATA, and VARYING CHARACTER FOR BIT DATA as VARYING CHARACTER. However, the ODBC Driver for DB2 returns these LONG and VARYING LONG data types if one reads a table with these data types. For example, when reading a table with a variable character string of length greater than 254 bytes, the ODBC Driver for DB2 returns a LONG VARCHAR.  
  
 The maximum length of the DB2 character and graphic string data types is dependent on the DB2 platform and version. For example, a CHAR type on DB2 for OS/390 V5R1 has a maximum length of 254 bytes, whereas a CHAR type on DB2/400 V4R4 has a maximum length of 32,766 bytes.  
  
 Data conversions from a large numeric type to a small numeric type are supported (from DOUBLE to SINGLE and from INT to SMALLINT, for example), however truncation and conversion errors can occur that will not be reported by the ODBC Driver for DB2.  
  
 Using the ODBC Driver for DB2, certain conversions of strings from EBCDIC to ASCII and then back to EBCDIC are asymmetric, and can result in strings that are different from the original. The EBCDIC specification contains ordinals for which there is no defined character. The ODBC Driver for DB2 translates all such undefined characters to the question mark character ("?"). So when ASCII strings containing these characters are converted back to EBCDIC, these undefined characters are replaced with question marks. To protect EBCDIC strings containing undefined characters, these fields should be tagged as binary strings and mapped by the application.  
  
 The affected ANSI-to-EBCDIC character conversions include the following:  
  
|Character value (decimal)|Character value (hexadecimal)|ANSI code page 1252|EBCDIC character after conversion to CCSID 37|  
|---------------------------------|-------------------------------------|-------------------------|---------------------------------------------------|  
|128|0x80|Not used|?|  
|130|0x82|Single low quote|?|  
|131|0x83|Latin F with hook|?|  
|132|0x84|Double low quote|?|  
|133|0x85|Ellipsis|?|  
|134|0x86|Dagger|?|  
|135|0x87|Double dagger|?|  
|136|0x88|Per mile|?|  
|137|0x89|S with caron|?|  
|138|0x8A|Left angle|?|  
|139|0x8B|Ligature OE|?|  
|140|0x8C|Not used|?|  
|142|0x8E|Not used|?|  
|145-156|0x91-0x9C||?|  
|158-159|0x9E-0x9F||?|