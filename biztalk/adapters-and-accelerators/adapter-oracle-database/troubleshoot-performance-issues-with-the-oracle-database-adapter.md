---
title: "Troubleshoot performance issues with the Oracle Database adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "performance issues, troubleshooting"
  - "troubleshooting, performance issues"
ms.assetid: 2035cd2e-ce87-419b-aada-61d257671623
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshoot performance issues with the Oracle Database adapter
This section discusses using troubleshooting techniques to resolve performance issues that you might encounter when using [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].  
  
## Known Issue  
 The following is the most common performance issue you might encounter when using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], along with its probable cause and resolution.  
  
##  <a name="BKMK_Slowdown"></a> Slowdown or stall in throughput when using the adapter with BizTalk Server  
 **Problem**  
  
 When using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the number of messages sent or received by the adapter slows down or comes to a stall.  
  
 **Cause**  
  
 The **EnableBizTalkCompatibilityMode** binding property is not set on the WCF-Custom send or receive port in BizTalk Server Administration console.  
  
 **Resolution**  
  
 Set the **EnableBizTalkCompatibilityMode** binding property to True. For more information about this property, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md). For instructions on how to set a binding property, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
### Possible memory leak on a 64-bit computer when using the Oracle database adapter to perform operations involving FLOAT data type  
 **Problem**  
  
 You may experience a memory leak when using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] on a 64-bit computer to perform operations that involve FLOAT data types.  
  
 **Resolution**  
  
 Install .NET \<*version*> (x64) on the 64-bit computer.  
  
## See Also  
[Troubleshoot the Oracle Database adapter.md](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)