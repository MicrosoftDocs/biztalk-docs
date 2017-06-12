---
title: "Samples for the Oracle Database adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "samples, WCF channel model"
  - "samples, WCF service model"
  - "samples, BizTalk"
  - "samples, migration"
ms.assetid: 744f19ce-3126-4745-92dd-4f68443180fc
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Samples for the Oracle Database adapter
Samples for [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] are categorized into:  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] samples  
  
-   WCF service model samples  
  
-   WCF channel model samples  
  
-   Migration samples  
  
 The samples are available at [http://go.microsoft.com/fwlink/p/?LinkID=196854](http://go.microsoft.com/fwlink/p/?LinkID=196854). The SQL scripts for creating the tables, packages, etc. used in the samples are also available along with the samples for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 The following list contains the names and descriptions of the samples for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
## BizTalk Server Samples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|Func_RecordTypes|Demonstrates how to use RECORD type parameters and return values in functions and procedures using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|Func_RefCursor|Demonstrates how to use REF CURSOR parameters in functions and procedures using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|InvokeFunction|Demonstrates how to invoke a function in Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|InvokeOverloadedProc|Demonstrates how to invoke with overloaded functions and procedures in Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|Operate_BFILE|Demonstrates how to use Oracle BFILE types in Oracle procedures using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|Operate_LOB|Demonstrates how to perform ReadLOB and UpdateLOB operations on tables with LOB data types using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|PollingQuery|Demonstrates how to configure a polling query and receive the results using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|SelectAccTable|Demonstrates how to perform a select query on an Oracle database table using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|SqlExec|Demonstrates how to perform parameterized queries using the SQLEXECUTE operation on an Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
  
## WCF Service Model Samples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|OracleBfileTypeSM|Demonstrates how to use Oracle BFILE types in basic SQL operations surfaced for Oracle tables and as parameters to Oracle procedures.|  
|OracleOverloadsSM|Demonstrates how to invoke overloaded functions and procedures in a package.|  
|OraclePollingSM|Demonstrates how to configure a polling query and receive the results.|  
|OracleRecordTypesSM|Demonstrates how to use RECORD type parameters and return values in functions and procedures.|  
|OracleRefCursorsSM|Demonstrates how to use REF CURSOR parameters in functions and procedures|  
|OracleTransactedDmlSM|Demonstrates how to perform operations on the Oracle database in a transaction using the WCF service model.|  
  
## WCF Channel Model Samples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|OraclePollingCM|Demonstrates how to configure a polling query and receive the results.|  
|OracleStreamingDemo|Demonstrates how to perform end-to-end streaming of LOB data using the UpdateLOB and table Select operations|  
|OracleTransactedDmlCM|Demonstrates how to perform operations on the Oracle database in a transaction using the WCF channel model.|  
  
## Migration Samples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|Oracle_Migration|Demonstrates how to use a BizTalk project created using the BizTalk ODBC Adapter for Oracle Database (shipped with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]) and make it work with the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] (shipped with [!INCLUDE[adapterpack20](../../includes/adapterpack20-md.md)]).|  
  
## See Also  
[Develop your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)