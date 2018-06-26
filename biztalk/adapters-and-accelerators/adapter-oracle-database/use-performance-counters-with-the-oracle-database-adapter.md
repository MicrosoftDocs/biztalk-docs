---
title: "Use performance counters with the Oracle Database adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "performance counters, using"
  - "performance counter, LOB Time Cumulative"
  - "performance counters, enabling"
  - "performance counters, and the WCF LOB Adapter SDK"
ms.assetid: beb80896-7594-411e-a83c-169d5278e2ce
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Use performance counters with the Oracle Database adapter
Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] clients can use performance counters to gauge the performance of the adapters. The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category **BizTalk .NET Adapter for Oracle DB** along with installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].  
  
## LOB Time (Cumulative) Performance Counter  
 The **BizTalk .NET Adapter for Oracle DB** category has one performance counter called the “LOB Time (Cumulative).” This performance counter denotes the time, in milliseconds, that the LOB client library takes to complete an action that the adapter initiates. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] creates an instance of the performance counter in any of the following patterns:  
  
```  
<process id>:<app domain id>:<oracle data source>:<string>  
```  
  
 Where "string" could be:  
  
- Connection.Open  
  
- Connection.Close  
  
- Metadata  
  
- Message action. For example, if the action is `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert` then the string will be SCOTT.Table.EMP.Insert.  
  
  The Oracle data source is the same as specified in the connection URI.  
  
  The performance counter is initialized only after the adapter makes the first call to the Oracle database. Also, the InstanceLifetime property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates. For more information about the `InstanceLifetime property`, see [http://go.microsoft.com/fwlink/p/?LinkId=104181](http://go.microsoft.com/fwlink/p/?LinkId=104181).  
  
> [!NOTE]
>  The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.  
  
## Enabling Performance Counters  
 The performance counters can be enabled or disabled by setting the binding property **EnablePerformanceCounters**. To enable performance counters, set the **EnablePerformanceCounters** binding property to **True**. To disable performance counters, set **EnablePerformanceCounters** to **False**. By default, **EnablePerformanceCounters** is set to **False**.  
  
## Performance Counters and the WCF LOB Adapter SDK  
 Changing the value of the **EnablePerformanceCounters** binding property also changes the value of the corresponding performance counter for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is dynamic. Therefore, if there are two instances of the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding in the AppDomain, and the **EnablePerformanceCounters** binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other. However, because the binding property for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False** depending on what value was specified last.  
  
## See Also  
[Troubleshoot the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)