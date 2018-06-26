---
title: "Oracle Database adapter samples | Microsoft Docs"
description: Oracle DB WCF adapter samples that can be used with BizTalk Server, WCF service model, and WCF channel model 
ms.custom: ""
ms.date: "10/18/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 744f19ce-3126-4745-92dd-4f68443180fc
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Samples for the Oracle Database adapter
Samples for [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] are categorized into:  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] samples  
  
- WCF service model samples  
  
- WCF channel model samples  

  
The samples are available at [BizTalk Adapter Pack 2010: Oracle Database adapter samples](https://www.microsoft.com/download/details.aspx?id=4675). The SQL scripts for creating the tables and packages used in the samples are included. 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
The following list describes the samples.
  
## BizTalk Server samples
  
| Sample Directory Name |                                                                                         Description                                                                                         |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Func_RecordTypes    |      Demonstrates how to use RECORD type parameters and return values in functions and procedures using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].      |
|    Func_RefCursor     |               Demonstrates how to use REF CURSOR parameters in functions and procedures using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].                |
|    InvokeFunction     |                        Demonstrates how to invoke a function in Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].                        |
| InvokeOverloadedProc  |         Demonstrates how to invoke with overloaded functions and procedures in Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].         |
|     Operate_BFILE     |                    Demonstrates how to use Oracle BFILE types in Oracle procedures using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].                     |
|      Operate_LOB      |       Demonstrates how to perform ReadLOB and UpdateLOB operations on tables with LOB data types using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].       |
|     PollingQuery      |                 Demonstrates how to configure a polling query and receive the results using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].                  |
|    SelectAccTable     |                 Demonstrates how to perform a select query on an Oracle database table using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].                 |
|        SqlExec        | Demonstrates how to perform parameterized queries using the SQLEXECUTE operation on an Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. |
  
## WCF service model samples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|OracleBfileTypeSM|Demonstrates how to use Oracle BFILE types in basic SQL operations surfaced for Oracle tables and as parameters to Oracle procedures.|  
|OracleOverloadsSM|Demonstrates how to invoke overloaded functions and procedures in a package.|  
|OraclePollingSM|Demonstrates how to configure a polling query and receive the results.|  
|OracleRecordTypesSM|Demonstrates how to use RECORD type parameters and return values in functions and procedures.|  
|OracleRefCursorsSM|Demonstrates how to use REF CURSOR parameters in functions and procedures|  
|OracleTransactedDmlSM|Demonstrates how to perform operations on the Oracle database in a transaction using the WCF service model.|  
  
## WCF channel model samples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|OraclePollingCM|Demonstrates how to configure a polling query and receive the results.|  
|OracleStreamingDemo|Demonstrates how to perform end-to-end streaming of LOB data using the UpdateLOB and table Select operations|  
|OracleTransactedDmlCM|Demonstrates how to perform operations on the Oracle database in a transaction using the WCF channel model.|  
  

## See Also  
[Develop your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)