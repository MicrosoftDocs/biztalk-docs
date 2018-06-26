---
title: "SQL adapter samples | Microsoft Docs"
description: SQL WCF adapter samples that can be used with BizTalk Server, WCF service model, and WCF channel model 
ms.custom: ""
ms.date: "10/18/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2438696-bc51-46df-81ca-00c17a52736e
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Samples for the SQL adapter

Samples for [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] are categorized into:  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] samples  
  
- WCF service model samples  
  
- WCF channel model samples  
  
The samples are available at [BizTalk Adapter Pack 2010: SQL adapter samples](https://www.microsoft.com/download/details.aspx?id=22455). The SQL scripts for creating the objects used in the samples, such as database, tables, and procedures are included. 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
The following list describes the samples.
  
## BizTalk Server samples  
  
|  Sample Directory Name  |                                                                                          Description                                                                                          |
|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ExecuteStoredProcedure  |      Demonstrates how to invoke a stored procedure in SQL Server database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] .      |
|       SelectTable       |  Demonstrates how to perform a Select operation on a SQL Server database table using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  |
|   CompositeOperations   |    Demonstrates how to perform composite operations on a SQL Server database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].    |
|      TypedPolling       |   Demonstrates how to perform strongly-typed polling on a SQL Server database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].   |
|   FILESTREAMOperation   | Demonstrates how to perform FILESTREAM operations on a SQL Server 2008 database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. |
| IncrementalNotification | Demonstrates how to receive incremental notification from a SQL Server database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. |
| Employee_PurchaseOrder  |                  Sample based on [Tutorial 2: Employee - Purchase Order Process using the SQL adapter](tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md).                  |
  
## WCF service model samples   
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|EmployeeBasicOps|Demonstrates how to perform Insert, Select, Update, and Delete operation on a SQL Server database using the adapter.|  
|ExecuteReader|Demonstrates how to invoke an ExecuteReader operation on a SQL Server database using the adapter.|  
|Execute_StoredProc|Demonstrates how to invoke a stored procedure in SQL Server database using the adapter.|  
|Execute_TypedStoredProcedure|Demonstrates how to invoke a strongly-typed stored procedure in SQL Server database using the adapter.|  
|Records_FILESTREAM_Op|Demonstrates how to update FILESTREAM data in a SQL Server database table using the adapter.|  
|ScalarFunction_ServiceModel|Demonstrates how to invoke scalar functions in a SQL Server database using the adapter.|  
|TableFunction_ServiceModel|Demonstrates how to invoke table-valued functions in a SQL Server database using the adapter.|  
|Polling_ServiceModel|Demonstrates how to receive polling-based data-changed messages from a SQL Server database using the adapter.|  
|TypedPolling_ServiceModel|Demonstrates how to receive strongly-typed polling-based data-changed messages from a SQL Server database using the adapter.|  
|Notification_ServiceModel|Demonstrates how to receive query notifications from a SQL Server database using the adapter.|  
  
## WCF channel model samples 
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|EmployeeInsertOp|Demonstrates how to perform an Insert operation on a SQL Server database using the adapter.|  
|Polling_ChannelModel|Demonstrates how to receive polling-based data-changed messages from a SQL Server database using the adapter.|  
  
## See Also  
[Develop your SQL applications](develop-your-sql-applications.md)