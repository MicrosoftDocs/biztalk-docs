---
title: "SAPClientFactory class in the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SAPClientFactory, supported methods and classes"
ms.assetid: e64de5e4-e53f-4708-ab02-9e12774e94cd
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SAPClientFactory class in the SAP adapter
The following section lists the methods and properties for the **SAPClientFactory** class. This is derived from **System.Data.Common.DbProviderFactory**.  
  
## Supported Properties  
  
|Name|Get/Set|Description|  
|----------|--------------|-----------------|  
|**Instance**|-|Singleton instance of SAPClientFactory|  
  
## Supported Methods  
  
|Name|Description|  
|----------|-----------------|  
|**CreateCommand()**|Creates an instance of SAPCommand|  
|**CreateConnection()**|Creates an instance of SAPConnection|  
|**CreateConnectionStringBuilder()**|Creates an instance of SAPConnectionStringBuilder|  
|**CreateParameter()**|Creates an instance of SAPParameter|  
  
## See Also  
 [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)