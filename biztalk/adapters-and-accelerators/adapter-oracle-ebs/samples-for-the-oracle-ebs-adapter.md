---
title: "Oracle EBS adapter samples | Microsoft Docs"
description: Oracle Enterprise Business Suite WCF adapter samples that can be used with BizTalk Server, WCF service model, and WCF channel model 
ms.custom: ""
ms.date: "10/18/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12f19f13-3b01-40d6-b12c-811f99841040
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Samples for the Oracle EBS adapter
Samples for [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] are categorized into:  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] samples  
  
- WCF service model samples  
  
- WCF channel model samples  
  
- Microsoft Office SharePoint Server samples  
  
  The samples are available at [BizTalk Adapter Pack 2010: Oracle E-Business Suite adapter samples](https://www.microsoft.com/download/details.aspx?id=6464). The SQL scripts for creating the interface tables, concurrent programs, tables, and packages used in the samples are included. 
  
> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
 The following list describes the samples. 
  
## BizTalk Server samples  
  
|    Sample Directory Name     |                                                                                                                                                                        Description                                                                                                                                                                        |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     InterfaceTableInsert     |                                                                                   Demonstrates how to insert records into an interface table in Oracle E-Business Suite using [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].                                                                                    |
|      ConcurrentProgram       |                                                                                       Demonstrates how to invoke a concurrent program in Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].                                                                                       |
|          RequestSet          |                                                                                          Demonstrates how to invoke a request set in Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].                                                                                           |
|      MsgContextProperty      | Demonstrates how to use the message context properties exposed by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to set application context to perform operations on artifacts in Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. |
| OracleEBS_CompositeOperation |                                                                                      Demonstrates how to perform composite operations in Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].                                                                                       |
|   OracleNotifyIncremental    |                                                                                   Demonstrates how to receive “incremental” query notification messages from Oracle using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].                                                                                    |
| PollingUsingSelectStatement  |                                                                            Demonstrates how to configure a polling query using a SELECT statement and receive the results using the   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].                                                                            |
|    PollingUsingStoredProc    |                                                                            Demonstrates how to configure a polling query using a stored procedure and receive the results using the   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].                                                                            |
  
## WCF Service model Sasamplesmples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|ConcProgram_ServiceModel|Demonstrates how to invoke concurrent programs in Oracle E-Business Suite using the adapter.|  
|ExecuteReader|Demonstrates how to invoke an ExecuteReader operation on Oracle E-Business Suite using the adapter.|  
|Interface_Table_Ops|Demonstrates how to perform operations on interface tables in Oracle E-Business Suite using the adapter.|  
|LargeDataTypes_ServiceModel|Demonstrates how to perform operations on tables with columns of large data types in Oracle E-Business Suite using the adapter.|  
|Notification_ServiceModel|Demonstrates how to receive notifications from databases behind Oracle E-Business Suite using the adapter.|  
|SelectPolling_ServiceModel|Demonstrates how to use a SELECT statement to poll an interface table in Oracle E-Business Suite using the adapter.|  
|StoredProcPolling_ServiceModel|Demonstrates how to use a stored procedure to poll tables in Oracle E-Business Suite using the adapter.|  
  
## WCF Channel model samples  
  
|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|InsertOperation|Demonstrates how to perform an Insert operation on an interface table in Oracle E-Business Suite using the adapter.|  
|SelectPolling_ChannelModel|Demonstrates how to use a SELECT statement to poll an interface table in Oracle E-Business Suite using the adapter.|  
  
## Microsoft Office SharePoint Server samples  
  
| Sample Directory Name |                                                                                                                                                                  Description                                                                                                                                                                   |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      MOSS_Sample      | Demonstrates how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to create a Windows Communication Foundation (WCF) service from Oracle E-Business Suite artifacts, and then use the WCF service to display data in Microsoft Office SharePoint Server using a Business Data List Web Part. |
  
## See Also  
[Develop your Oracle E-Business Suite applications](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)