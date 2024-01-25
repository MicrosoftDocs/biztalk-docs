---
description: "Learn more about: SAPDataReader class in the SAP adapter"
title: "SAPDataReader class in the SAP adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
