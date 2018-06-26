---
title: "Use Performance Counters with the Oracle E-Business Suite adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7d722b7-8343-4956-81ed-acd5a463a9b1
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Use Performance Counters with the Oracle E-Business Suite adapter
Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] clients can use performance counters to gauge the performance of the adapters. The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category **BizTalk .NET Adapter for Oracle E-Business Suite** along with installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].  
  
## LOB Time (Cumulative) performance counter  
 The **BizTalk .NET Adapter for Oracle E-Business Suite** category has one performance counter called the “LOB Time (Cumulative).” This performance counter denotes the time, in milliseconds, that the LOB client library takes to complete an action that the adapter initiates. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] creates an instance of the performance counter in any of the following patterns:  
  
```  
<process id>:<app domain id>:<oracle data source>:<string>  
```  
  
 Where "string" could be:  
  
- Connection.Open  
  
- Connection.Close  
  
- Metadata  
  
- Message action. For example, if the action is `InterfaceTables/Insert/FND/APPS/MS_SAMPLE_EMPLOYEE` then the string will be InterfaceTables.Insert.FND.APPS.MS_SAMPLE_EMPLOYEE.  
  
  The Oracle data source is the same as specified in the connection URI.  
  
  The performance counter is initialized only after the adapter makes the first call to the Oracle database. Also, the InstanceLifetime property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates. 
  
> [!NOTE]
>  The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.  
  
## Enabling Performance Counters  
 The performance counters can be enabled or disabled by setting the binding property **EnablePerformanceCounters**. To enable performance counters, set the **EnablePerformanceCounters** binding property to **True**. To disable performance counters, set **EnablePerformanceCounters** to **False**. By default, **EnablePerformanceCounters** is set to **False**.  
  
## Performance Counters and the WCF LOB Adapter SDK  
 Changing the value of the **EnablePerformanceCounters** binding property also changes the value of the corresponding performance counter for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is dynamic. Therefore, if there are two instances of the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding in the AppDomain, and the **EnablePerformanceCounters** binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other. However, because the binding property for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False** depending on what value was specified last.  
  
## See Also  
[Troubleshooting the adapter](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)