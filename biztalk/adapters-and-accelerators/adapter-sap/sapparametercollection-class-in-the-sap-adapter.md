---
description: "Learn more about: SAPParameterCollection class in the SAP adapter"
title: "SAPParameterCollection class in the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SAPParameterCollection, supported methods and classes"
ms.assetid: fd09355b-95f4-4d49-a643-b13058e63d74
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SAPParameterCollection class in the SAP adapter
The following section lists the methods and properties for the **SAPParameterCollection** class. This is derived from **System.Data.Common.DbParameterCollection**.  
  
## Supported Properties  
  
|Name|Get/Set|Description|  
|----------|--------------|-----------------|  
|**Count**|Get|Number of parameters in the collection.|  
|**IsFixedSize**|Get|Not supported. Returns false.|  
|**IsReadOnly**|Get|Not supported. Returns false.|  
|**IsSynchronized**|Get|Not supported. Returns false.|  
|**SyncRoot**|Get|Returns the lock object.|  
  
## Supported Methods  
  
|Name|Description|  
|----------|-----------------|  
|**Add(SAPParameter)**|Parameter cannot belong to more than one ParameterCollection.|  
|**Add(object)**|Object should be of SAPParameter type.|  
|**AddRange(System.Array)**|Adds an array of SAPParameter instances.|  
|**Clear()**|Clears the parameters in the collection.|  
|**Contains(object)**|Checks based on parameter instance.|  
|**Contains(string)**|Checks based on parameter name.|  
|**CopyTo(SAPParameter[], int)**|Copies parameter list to an array of SAPParameter types.|  
|**CopyTo(System.Array, int)**|Copies parameter list to an array.|  
|**GetEnumerator()**|Gets an enumerator for the parameters in the collection.|  
|**IndexOf(object)**|Index of parameter based on SAPParameter instance.|  
|**IndexOf(string)**|Index of parameter based on SAPParameter name.|  
|**Insert(int, object)**|Inserts an SAPParameter into the collection.|  
|**Remove(object)**|Removes an SAPParameter into the collection based on instance.|  
|**RemoveAt(int)**|Removes an SAPParameter into the collection at a given index.|  
|**RemoveAt(string)**|Removes an SAPParameter into the collection based on name.|  
  
## See Also  
 [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)
