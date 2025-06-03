---
description: "Learn more about: Streaming Support for LOB Data Types in Oracle Database"
title: "Streaming Support for LOB Data Types in Oracle Database"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Streaming Support for LOB Data Types in Oracle Database
The Oracle database supports streaming on large object (LOB) data types. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]supports message streaming, which makes it possible to stream LOB data end-to-end between the Oracle database and an adapter client. However, streaming is not supported in the same manner across all programming models when you use the adapter.  
  
 The following shows how end-to-end streaming of LOB data types is supported by the adapter across different programming models.  
  
|Operation|WCF Channel Model|WCF Service Model|BizTalk Server|  
|---------------|-----------------------|-----------------------|--------------------|  
|Table/View Insert operation|Not supported|Not supported|Not supported|  
|Table/View Select operation|Supported|Not supported|Supported|  
|Table/View Update operation|Not supported|Not supported|Not supported|  
|Table/View Delete operation|Not supported|Not supported|Not supported|  
|Table/View ReadLOB operation|Supported; however, the ReadLOB operations is surfaced primarily to support streaming in the WCF service model, it is not recommended for use in the WCF channel model. Use a Select operation or the SQLEXECUTE operation instead.|Supported|The ReadLOB operation is not supported for BizTalk Server. Use a Select operation instead.|  
|Table/View UpdateLOB operation|Supported|Not Supported|Supported|  
|SQLEXECUTE operation|Supported in the response|Not Supported|Supported in the response|  
|Stored procedure and function operation|Supported in the response|Not Supported|Supported in the response|  
|POLLINGSTMT operation|Supported|Not Supported|Supported|  
  
 For more comprehensive information about how streaming of LOB data types is supported by the adapter and how it is supported when you use various programming models with the adapter, see [Streaming large object data types](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).  
  
## See Also  
 [Overview of BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)
