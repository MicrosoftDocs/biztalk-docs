---
title: "SAPDataReader class in the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SAPDataReader, supported methods and classes"
ms.assetid: bd0e55ea-7413-498f-851f-ed97bd8bacab
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SAPDataReader class in the SAP adapter
The following section lists the methods and properties for the **SAPDataReader** class. This is derived from **System.Data.Common.DbDataReader**.  
  
## Supported Properties  
  
|Name|Get/Set|Description|  
|----------|--------------|-----------------|  
|**Depth**|Get|Not supported. Returns 0.|  
|**FieldCount**|Get|Number of fields in the current record set|  
|**IsClosed**|Get|Returns status of data reader|  
|**RecordsAffected**|Get|Not supported. Returns -1|  
  
## Supported Methods  
  
|Name|Description|  
|----------|-----------------|  
|**Close()**|Closes the DataReader|  
|**Get [methods]** <sup>*</sup><br /><br /> where [methods] is the expected data type. E.g. GetInt32(int)|Gets column value based on the data type expected|  
|**IsDBNull(int)**|Not supported. Returns false.|  
  
## See Also  
 [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)