---
title: "Support for Composite Operations2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f65cf10-4e27-4872-bc6a-defe6cbab198
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Support for Composite Operations
The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] enables adapter clients to perform composite operations that can include any number of the following operations, and in any order:  
  
- Select, Insert, Update, and Delete operations on an interface table and database table.  
  
- Select operation on an interface view and database view.  
  
- Stored procedures, functions, and procedures within packages that are surfaced as operations in the adapter.  
  
  The operations in a composite operation can target tables and views in the same database or different databases. However, data cannot be shared or reused across different operations in a composite operation. For example, in a composite operation, the result set of a Select operation cannot be used as the input parameter for a stored procedure.  
  
  Each operation in a composite operation is performed using a separate connection. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] consumes as many connections from the ODP.NET connection pool as the number of operations in a composite operation, and then releases the connections as the operations get executed. However, if an operation in the composite operation returns a result set, the connection is released only after the message is consumed.  
  
> [!IMPORTANT]
>  If you experience time-out issues while executing a composite operation then it could be because the number of connections is less than the number of operations in a composite operation involving:  
> 
> - Stored procedures containing BFILE, BLOB, CLOB, NCLOB, and REF CURSOR as OUT or IN OUT parameters.  
>   -   Select operation.  
> 
>   To resolve this issue, you must ensure that if there are “n” number of such operations in a composite operation, the value specified for the **MinPoolSize** binding property is “n+1” or greater. For more information about the **MinPoolSize** binding property, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
 For information about:  
  
- How to perform composite operations in [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see  [Run Composite Operations on Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).  
  
- Message schemas for the composite operation, see [Message Schemas for the Composite Operation](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-composite-operation1.md).  
  
> [!NOTE]
>  You can also set the applications context for composite operations in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. It is mandatory to set the applications context for the composite operations if any of the operations in a composite operation is performed on an interface table or interface view. For information about applications context, and how to set it, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
## See Also  
 [What operations are supported by the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/what-operations-are-supported-by-the-oracle-e-business-suite-adapter.md)