---
description: "Learn more about: Support for ODBC 2 Level 2 Functions"
title: "Support for ODBC 2 Level 2 Functions"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Support for ODBC 2 Level 2 Functions
The following table lists the ODBC 2.*x* level 2 functions that are supported by the Microsoft ODBC Driver for DB2.  
  
|ODBC 2.*x* level 2 functions supported|Functions supported by the Microsoft ODBC Driver for DB2|  
|--------------------------------------------|--------------------------------------------------------------|  
|**SQLBrowseConnect**|No|  
|**SQLColumnPrivileges**|No|  
|**SQLDataSources**|Yes. This function is actually supported by the ODBC Driver Manager|  
|**SQLDescribeParam**|No|  
|**SQLDrivers**|Yes. This function is actually supported by the ODBC Driver Manager|  
|**SQLExtendedFetch**|Yes, but supports forward scrolling only|  
|**SQLForeignKeys**|No|  
|**SQLMoreResults**|Yes|  
|**SQLNativeSQL**|Yes|  
|**SQLNumParams**|Yes|  
|**SQLParamOptions**|Yes|  
|**SQLPrimaryKeys**|Yes, but SQL grammar conformance varies depending on the version of the DB2 database that is accessed|  
|**SQLProcedureColumns**|Yes|  
|**SQLProcedures**|Yes|  
|**SetPos**|Yes|  
|**SQLSetScrollOptions**|Yes|  
|**SQLTablePrivileges**|No|
