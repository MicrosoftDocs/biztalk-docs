---
title: "Support for ODBC Statement Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc6058f2-39f5-4dc2-bed9-b2f7279c0066
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Support for ODBC Statement Attributes
The following table lists the ODBC statement attribute support using the Microsoft ODBC Driver for DB2. Note that the statement attributes in this list use the ODBC Version 3.0 attribute names, rather than the older ODBC 1.0 names.  
  
|ODBC statement attribute|ODBC version|Attribute supported by the Microsoft ODBC Driver for DB2|  
|------------------------------|------------------|--------------------------------------------------------------|  
|SQL_ATTR_APP_PARAM_DESC|3.0|Yes|  
|SQL_ATTR_APP_ROW_DESC|3.0|Yes|  
|SQL_ATTR_ASYNC_ENABLE|1.0|No|  
|SQL_ATTR_CONCURRENCY||No|  
|SQL_ATTR_CURSOR_SCROLLABLE|3.0|No|  
|SQL_ATTR_CURSOR_SENSITIVITY|3.0|No|  
|SQL_ATTR_CURSOR_TYPE|1.0|Yes, but the ODBC Driver for DB2 supports a forward scrolling only cursor type|  
|SQL_ATTR_ENABLE_AUTO_IPD|3.0|No|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|3.0|No|  
|SQL_ATTR_IMP_PARAM_DESC||Yes, handled by ODBC Driver Manager|  
|SQL_ATTR_IMP_ROW_DESC||Yes, handled by ODBC Driver Manager|  
|SQL_ATTR_KEYSET_SIZE|1.0|No|  
|SQL_ATTR_MAX_LENGTH|1.0|No|  
|SQL_ATTR_MAX_ROWS|1.0|No|  
|SQL_ATTR_METADATA_ID|3.0|Yes|  
|SQL_ATTR_NOSCAN|1.0|Yes|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|3.0|Yes|  
|SQL_ATTR_PARAM_BIND_TYPE|3.0|Yes|  
|SQL_ATTR_PARAM_OPERATION_PTR|3.0|Yes|  
|SQL_ATTR_PARAM_STATUS_PTR|3.0|Yes|  
|SQL_ATTR_PARAMS_PROCESSED_PTR|3.0|Yes|  
|SQL_ATTR_PARAMSET_SIZE|3.0|Yes|  
|SQL_ATTR_QUERY_TIMEOUT|1.0|No|  
|SQL_ATTR_RETRIEVE_DATA|1.0|No|  
|SQL_ATTR_ROW_ARRAY_SIZE|3.0|Yes|  
|SQL_ATTR_ROW_BIND_OFFSET_PTR|3.0|Yes|  
|SQL_ATTR_ROW_BIND_TYPE|1.0|Yes|  
|SQL_ATTR_ROW_NUMBER|1.0|No|  
|SQL_ATTR_ROW_OPERATION_PTR|3.0|No|  
|SQL_ATTR_ROW_STATUS_PTR|3.0|Yes|  
|SQL_ATTR_ROWS_FETCHED_PTR|3.0|Yes|  
|SQL_ATTR_SIMULATE_CURSOR|1.0|No|  
|SQL_ATTR_USE_BOOKMARKS|1.0|No|