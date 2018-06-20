---
title: "Errors Returned by the ODBC Driver for DB2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5def0d7-93c4-42c1-bf83-1b72c85cd391
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Errors Returned by the ODBC Driver for DB2
The ODBC Driver for DB2 generates errors in the following areas:  
  
- ODBC Driver Manager  
  
- Microsoft ODBC Driver for DB2  
  
- DRDA Application Requester network client  
  
  The ODBC Driver Manager is a shared library that establishes connections with ODBC drivers, submits requests to ODBC drivers, and returns results to applications. An ODBC Driver Manager error has the following format:  
  
```  
[vendor] [ODBC DLL] message  
```  
  
 For example:  
  
```  
[Microsoft] [ODBC DLL] Driver does not support this function.  
```  
  
 If you encounter this type of error, check the last ODBC call the application made for possible problems. For further information on ODBC Driver Manager errors, contact your ODBC application vendor or refer to the ODBC documentation available from Microsoft Press.  
  
 An error reported by the Microsoft ODBC Driver for DB2 has the following format:  
  
```  
[Microsoft] [ODBC Driver for DB2] message  
  
```  
  
 For example:  
  
```  
[Microsoft] [ODBC Driver for DB2] Invalid precision specified.  
```  
  
 If you encounter this type of error is, check the last ODBC call the application made for possible problems. For further information on ODBC Driver errors, contact your ODBC application vendor or refer to the ODBC documentation available from Microsoft Press.  
  
 When using the Microsoft ODBC Driver for DB2, data source refers to the target database. An error that occurs in the data source is returned with the data source name and in the following format:  
  
```  
[Microsoft] [ODBC Driver for DB2] [data_source] message  
```  
  
 For example, an ODBC application may receive the following message from a DB2 data source running on an IBM mainframe:  
  
```  
[Microsoft] [ODBC Driver for DB2] [DB2] DB2-0919: specified length too long for CHAR column  
```  
  
 If you encounter this type of error, the application attempted to perform an operation not supported by the DB2 database system. Check the DB2 database system documentation for more information or consult your database administrator.