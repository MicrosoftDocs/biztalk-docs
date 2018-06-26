---
title: "Use Performance Counters with the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae381b78-d89e-4cf2-810b-821e49422463
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Use Performance Counters with the SQL adapter
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] clients can use the performance counters to gauge the performance of the adapters. The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category "[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]" along with the Adapter Pack installation.  
  
## The LOB Time (Cumulative) Performance Counter  
 The **BizTalk .NET Adapter for SQL** category has one performance counter called "LOB Time (Cumulative)". This performance counter denotes the time, in milliseconds, that the SQL Server client library takes to complete an action that the adapter initiates. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] creates an instance of the performance counter for each action, for a specific SQL Server instance and database name. The instances are created in the following pattern:  
  
```  
<processId>:<appDomainId>:<endpointId>:<actionId>  
```  
  
 The `<endpointId>` is derived as `<sql_server_name>, <instance_name>, <database_name>`.  
  
 The \<actionId\> is derived in the following manner:  
  
- For opening a connection, the action ID is “Open”.  
  
- For inbound operations, the action ID is “Inbound”.  
  
- For outbound operations, the action ID is the action of the operation being invoked, with “/” replaced by an underscore “_”. Also, the action ID is prefixed with the “ExecuteScalar”, “ExecuteReader”, or “ExecuteNonQuery” depending on the method that the adapter internally uses to perform the operation on the SQL Server database. For example, the adapter internally uses the **ExecuteReader** method to execute a stored procedure in SQL Server. So, the action ID for the stored procedure, MyProcedure, will be:  
  
  ```  
  ExecuteReader_Procedure_dbo_MyProcedure  
  ```  

  The performance counter is initialized only after the adapter makes the first call to the SQL Server database. Also, the [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx) property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates.
  
> [!NOTE]
>  The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.  
  
## Enabling Performance Counters  
 The performance counters can be enabled or disabled by setting the binding property **EnablePerformanceCounters**. To enable performance counters, set the **EnablePerformanceCounters** binding property to **True**. To disable performance counters, set **EnablePerformanceCounters** to **False**. By default, the property is set to **False**. For more information about this binding property, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
## Performance Counters and the WCF LOB Adapter SDK  
 Changing the value of the **EnablePerformanceCounters** binding property also changes the value of the corresponding performance counter for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is dynamic. Hence, if there are two instances of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding in the application domain, and the **EnablePerformanceCounters** binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other. However, because the binding property for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False** depending on what value was specified last.  
  
## See Also  
[Troubleshoot the SQL adapter](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)