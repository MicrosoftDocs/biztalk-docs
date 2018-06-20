---
title: "Features for SQL adapter clients | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f638154b-0a09-4f89-9c52-2a62fafec7dc
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Features for SQL adapter clients
In addition to the features discussed throughout the topics of [Overview of BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md), the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] also provides the following features that are useful for adapter clients:  
  
- **Support for configuring adapters using binding properties**. Adapter clients can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] by specifying certain binding properties. For example, clients can specify the maximum number of connections allowed in a connection pool for a specific connection string by setting the **MaxConnectionPoolSize** binding property. For more information, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
- **Support for null values for operation parameters**. Adapter clients can provide null values for operation parameters using the XSD "nillable" attribute.  
  
- **Support for dynamic ports in BizTalk**. Through the BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports a dynamic port that enables dynamic routing of messages from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] based on the message context properties. For more information, see [Configure dynamic ports](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md).  
  
- **Support for performance counters**. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports WCF-based performance counters for use by adapter clients. For more information about performance counters, see [Use Performance Counters with the SQL adapter](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md).  
  
## See Also  
 [Overview of BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)