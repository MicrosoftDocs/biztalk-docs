---
title: "Troubleshooting the ODBC Driver for DB2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6634aaef-6647-4454-8659-f030b53610ee
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Troubleshooting the ODBC Driver for DB2
The Windows 2000 Event Viewer can be a useful tool for troubleshooting data access in some cases. The ODBC Driver for DB2 does not issue events. However, when SNA (APPC/LU 6.2) is used for the network transport for the ODBC Driver for DB2, the low-level SNA APPC transport issues events on the SNA connection.  
  
 The ODBC Driver for DB2 supplied with Host Integration Server has the ability to trace DRDA data flows when used over TCP/IP. This capability is accessible from the SNADB2 Service tracing inside the Trace utility shipped with Host Integration Server.  
  
 This facility shows the same data as an APPC trace but without the control indicators (for example, What_Received). Socket errors are traced and the error codes can be looked up in Winsock2.h supplied with the Win32 SDK.  
  
 When the ODBC Driver for DB2 passes an error code, the best source in which to look-up the meaning of the return code is often the SQL Reference or SQL Messages and Codes Reference for the target SQL database. In this case, the target database is one of the DB2 platforms supported by the ODBC Driver for DB2.  
  
 The ODBC Driver for DB2 maintains an internal integer variable named SQLCODE and an internal 5-byte character string variable named SQLSTATE used to check the execution of SQL statements on DB2. SQLCODE is set by DB2 after each SQL statement is executed. DB2 returns the following values for SQLCODE:  
  
- If SQLCODE = 0, execution was successful.  
  
- If SQLCODE > 0, execution was successful with a warning.  
  
- If SQLCODE < 0, execution was not successful.  
  
- SQLCODE = 100, "no data" was found. For example, a **FETCH** statement returned no data because the cursor was positioned after the last row of the result table.  
  
  SQLSTATE is also set by DB2 after the execution of each SQL statement. Application programs can check the execution of SQL statements by testing SQLSTATE instead of SQLCODE. SQLSTATE provides application programs with common codes for common error conditions (the values of SQLSTATE are product-specific only if the error or warning is product-specific). Furthermore, SQLSTATE is designed so that application programs can test for specific errors or classes of errors.  
  
  SQLSTATE values consist of a two-character class code value, followed by a three-character subclass code value. The first character of an SQLSTATE value indicates whether the SQL statement was executed successfully or unsuccessfully (equal to or not equal to zero, respectively). Class code values represent classes of successful and unsuccessful execution conditions. The following table describes SQLSTATE class codes used by DB2.  
  
|Class Code|Description of Error Class|  
|----------------|--------------------------------|  
|**00**|Successful completion. Execution of the SQL statement was successful and did not result in any type of warning or exception condition.|  
|**01**|Warning|  
|**02**|No data|  
|**07**|Dynamic SQL error|  
|**08**|Connection exception|  
|**0A**|Feature not supported|  
|**0F**|Invalid token|  
|**21**|Cardinality violation|  
|**22**|Data exception|  
|**23**|Constraint violation|  
|**24**|Invalid cursor state|  
|**25**|Invalid transaction state|  
|**26**|Invalid SQL statement identifier|  
|**2D**|Invalid transaction termination|  
|**34**|Invalid cursor name|  
|**39**|External function call exception|  
|**40**|Transaction rollback|  
|**42**|Syntax error or access rule violation|  
|**44**|WITH CHECK OPTION violation|  
|**51**|Invalid application state|  
|**53**|Invalid operand or inconsistent specification|  
|**54**|SQL or product limit exceeded|  
|**55**|Object not in prerequisite state|  
|**56**|Miscellaneous SQL or product error|  
|**57**|Resource not available or operator intervention|  
|**58**|System error|  
  
 The SQLSTATE value of HY000 is defined as a driver-specific error. An SQLSTATE of 08S01 (connection exception with a subclass code of S01) also indicates a driver-specific error. This means the SQLCODE should be looked up in the driver-specific documentation included with the ODBC Driver for DB2.  
  
 If the SQLSTATE does not indicate a driver-specific error when the ODBC Driver for DB2 passes back an SQLSTATE of 08S01, it indicates a network error. For example, an SQLCODE of -603 is a driver-specific error that is mapped to DB2OLEDB_COMM_HOST_CONNECT_FAILED in the db2oledb.h include file supplied with the ODBC Driver for DB2. Errors with an SQLSTATE of 08S01 are documented in the db2oledb.h include file (the SQLCODE value) which is located on the Host Integration Server CD in the SDK\Include subdirectory.  
  
 The following steps are useful in researching an error. Start by reading the provided error text returned by the ODBC Driver for DB2. In some cases, the error text may provide limited information. For example, error text from an SQLCODE of -603 reads:  
  
```  
Test connection failed because of an error in initializing driver.  
Could not connect to specified host.   
```  
  
 The next step is to lookup the SQLSTATE to determine the source of the error. Is the error a DB2 error, a network client error, or an ODBC Driver error? An SQLSTATE of 08S01 is defined as follows:  
  
```  
Communication link failure.  
```  
  
 This definition is intended to inform the user, administrator, or developer that the error is one related to the ODBC driver's underlying network client.  
  
 Unfortunately, many of the SQLSTATE codes returned by the ODBC Driver for DB2 are DB2 errors and are not documented in the ODBC Driver for DB2 Help.  
  
 The SQLSTATE of HY000 is defined as a driver-specific error. An SQLSTATE of 08S01 also indicates a driver-specific error. In this case, you should look up the SQLCODE in the driver-specific documentation included with the ODBC Driver for DB2.  
  
 If the SQLSTATE does not indicate a driver-specific error, you should look up the SQLCODE in the appropriate DB2 manual for the target platform. For example, an SQLCODE of -603 is documented in Appendix B, "SQLCODEs and SQLSTATEs," in the *AS/400 Advanced Series DB2 for AS/400 SQL Programming, Version 4*, document number SC41-5611-00 published by IBM. An SQLCODE of -603 corresponds to SQLSTATE 23515 in the DB2 for OS/400 error code list. For example, the explanation for this SQLCODE is:  
  
```  
Unique index cannot be created because of duplicate keys.   
```  
  
 When the SQLSTATE and the SQLCODE definitions documented in these appendixes create a mismatch with the actual errors returned, it usually indicates a driver-specific error condition.  
  
 A final step in understanding an error is to check the db2oledb.h file. This file is not installed by Setup for the Host Integration Client 2000, but is located on the CD-ROM for in the SDK\Include folder. An SQLCODE (for example, -603) can be found by searching the rightmost column of the db2oledb.h file for a value near to 603. For instance, locate the comment "/* -600 \*/" and then count down three additional lines to line number 603. The internal error code -603 is defined as follows:  
  
```  
DB2OLEDB_COMM_HOST_CONNECT_FAILED.  
```  
  
 This particular error usually indicates a problem with the configuration parameters or the connection string passed.