---
title: "Support for ODBC Connection Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6df5a7ab-e911-4a19-bd17-f5f9656b3ae6
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Support for ODBC Connection Attributes
The following table lists the ODBC connection attributes support using the Microsoft ODBC Driver for DB2. Note that the connection attributes in this list use the ODBC Version 3.0 attribute names, rather than the older ODBC 1.0 names.  
  
|ODBC connection attribute|ODBC version|Attribute supported by the Microsoft ODBC Driver for DB2|  
|-------------------------------|------------------|--------------------------------------------------------------|  
|SQL_ATTR_ACCESS_MODE|1.0|Yes|  
|SQL_ATTR_ASYNC_ENABLE|3.0|No|  
|SQL_ATTR_AUTO_IPD|3.0|No|  
|SQL_ATTR_AUTOCOMMIT|1.0|Yes|  
|SQL_ATTR_CONNECTION_DEAD|3.5|No|  
|SQL_ATTR_CONNECTION_TIMEOUT|3.0|No|  
|SQL_ATTR_CURRENT_CATALOG|2.0|Yes|  
|SQL_ATTR_ENLIST_IN_DTC|3.0|Yes|  
|SQL_ATTR_ENLIST_IN_XA|3.0|No|  
|SQL_ATTR_LOGIN_TIMEOUT|1.0|No|  
|SQL_ATTR_METADATA_ID|3.0|No|  
|SQL_ATTR_ODBC_CURSORS|2.0|Yes, handled by ODBC Driver Manager|  
|SQL_ATTR_PACKET_SIZE|2.0|No|  
|SQL_ATTR_QUIET_MODE|2.0|Yes|  
|SQL_ATTR_TRACE|1.0|Yes, handled by ODBC Driver Manager|  
|SQL_ATTR_TRACEFILE|1.0|Yes, handled by ODBC Driver Manager|  
|SQL_ATTR_TRANSLATE_LIB|1.0|No|  
|SQL_ATTR_TRANSLATE_DLL|1.0|No|  
|SQL_ATTR_TRANSLATE_OPTION|1.0|No|  
|SQL_ATTR_TXN_ISOLATION|1.0|Yes|