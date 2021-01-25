---
description: "Learn more about: SiebelClientFactory class in the Siebel adapter"
title: "SiebelClientFactory class in the Siebel adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SiebelClientFactory"
  - "Data Provider for Siebel, SiebelClientFactory"
  - "SiebelClientFactory, supported properties and methods"
ms.assetid: f3a807d3-a030-47d8-b145-e18075ec353c
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SiebelClientFactory class in the Siebel adapter
An ADO.NET client accesses the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] using generic ADO.NET classes and interfaces. To enable this feature, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] inherits the **System.Data.Common.DbProviderFactory** class. The client program consumes the client as follows:  
  
```  
  
DbProviderFactory factory = DbProviderFactories.GetFactory("Microsoft.Data.SiebelClient");  
DbConnection connection = factory.CreateConnection();  
```  
  
 An alternative approach is as follows:  
  
```  
SiebelClientFactory factory = SiebelClientFactory.Instance;  
DbConnection connection = factory.CreateConnection();  
```  
  
 SiebelClientFactory exists in the namespace Microsoft.Data.SiebelClient.  
  
## Supported Members  
 **SiebelClientFactory** extends **System.Data.CommonDbProviderFactory**.  The following table provides a description of the members that **SiebelClientFactory** overrides.  
  
|Name|Description|  
|----------|-----------------|  
|**Instance**|This is a member variable.  It provides a singleton instance of SiebelClientFactory.|  
|**CreateCommand()**|Creates an instance of SiebelCommand.|  
|**CreateConnection()**|Creates an instance of SiebelConnection.|  
|**CreateConnectionStringBuilder()**|Creates an instance of SiebelConnectionStringBuilder.|  
|**CreateParameter()**|Creates an instance of SiebelParameter.|  
  
## See Also  
 [Extend ADO.NET Interfaces with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)
