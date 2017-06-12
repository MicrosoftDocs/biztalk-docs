---
title: "SAPCommand class in the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SAPCommand, supported methods, classes, and constructors"
ms.assetid: 55ad334e-1cc3-47c1-8764-be0f4e93f8b5
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SAPCommand class in the SAP adapter
This command represents a SQL query to be executed on the SAP backend. The [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] currently supports SELECT and EXEC statements only. SELECT statements enable extraction of data from a single SAP table, and EXEC statements enable users to execute RFCs on the SAP server.  
  
 This is derived from **System.Data.Common.DbCommand**.  
  
## Supported Properties  
  
|Name|Get/Set|Description|  
|----------|--------------|-----------------|  
|**CommandText**|Get and Set|Supports SELECT and EXEC statements. For more information about the SELECT statement, see [Syntax for a SELECT Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md). For more information about the EXEC statement, see [Syntax for an EXEC Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-exec-statement-in-sap.md).|  
|**CommandTimeout**|Get and Set|Not supported.|  
|**CommandType**|Get and Set|CommandType.Text supported.|  
|**Connection**|Get and Set|The underlying SAP connection on which the command will be executed.|  
|**DesignTimeVisible**|Get|Not supported. Returns false.|  
|**Parameters**|Get|Parameter collection used for this command.|  
|**UpdatedRowSource**|-|Not supported.|  
  
## Supported Methods  
  
|Name|Description|  
|----------|-----------------|  
|**Cancel()**|Cancels the command while retrieving data in batches. Cancellation happens after a batch is retrieved.|  
|**ExecuteNonQuery()**|Does not output any DataReader. However, values will be available via bound parameters.|  
|**ExecuteReader()**|Outputs a DataReader with all complex type Export and Table parameters as resultsets. The values can also be obtained via bound parameters.|  
|**ExecuteReader(CommandBehavior)**|CommandBehaviors supported are:<br /><br /> -   Default<br />-   SingleResult<br />-   SingleRow<br />-   SchemaOnly|  
|**ExecuteScalar()**|Maps to:<br /><br /> -   CommandBehaviour.SingleRow for SELECT statements.<br />-   CommandBehaviour.SingleResult for EXEC statements.|  
|**Prepare()**|-   EXEC supports bind parameters.<br />-   SELECT supports bind parameters.|  
  
## Supported Constructors  
  
|Name|Description|  
|----------|-----------------|  
|**SAPCommand()**|Create a new instance of SAPCommand.|  
|**SAPCommand(string)**|SAPCommand with command text.|  
|**SAPCommand(string, SAPConnection)**|SAPCommand with command text and the SAPConnection object using which the command will be executed|  
  
## See Also  
 [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)