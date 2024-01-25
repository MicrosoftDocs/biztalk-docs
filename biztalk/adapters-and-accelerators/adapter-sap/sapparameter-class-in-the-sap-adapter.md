---
description: "Learn more about: SAPParameter class in the SAP adapter"
title: "SAPParameter class in the SAP adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SAPParameter class in the SAP adapter
The following section lists the methods and properties for the **SAPParameter** class. This is derived from **System.Data.Common.DbParameter**.  
  
## Supported Properties  
  
|Name|Get/Set|Description|  
|----------|--------------|-----------------|  
|**DbType**|Get|DbType if the parameter returned. Cannot be set.|  
|**Direction**|Get and Set|ParameterDirection.ReturnValue not supported.|  
|**IsNullable**|-|Not supported.|  
|**ParameterName**|Get and Set|Name of the parameter.|  
|**Size**|-|Not supported.|  
|**SourceColumn**|-|Not supported.|  
|**SourceColumnNullMapping**|-|Not supported.|  
|**SourceVersion**|-|Not supported.|  
|**Value**|Get and Set|Value of the parameter|  
  
## Supported Methods  
  
|Name|Description|  
|----------|-----------------|  
|**ResetDbType()**|Not supported.|  
  
## Supported Constructors  
  
|Name|Description|  
|----------|-----------------|  
|**SAPParameter()**|SAP parameter instance.|  
|**SAPParameter(string)**|SAP parameter with SAP parameter name.|  
|**SAPParameter(string, DbType)**|SAP parameter with SAP parameter name and DbType.|  
|**SAPParameter(string, object)**|SAP parameter with SAP parameter name and value. Complex types have value of type DataTable and XML string.|  
|**SAPParameter(string, ParameterDirection)**|SAP parameter with SAP parameter name and parameter direction.|  
  
## See Also  
 [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)
