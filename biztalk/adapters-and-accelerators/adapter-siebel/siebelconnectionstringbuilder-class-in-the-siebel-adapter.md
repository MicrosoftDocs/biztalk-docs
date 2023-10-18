---
description: "Learn more about: SiebelConnectionStringBuilder class in the Siebel adapter"
title: "SiebelConnectionStringBuilder class in the Siebel adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SiebelConnectionStringBuilder class in the Siebel adapter
The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] provides a `DbConnectionStringBuilder` implementation to enable SQL Server Integration Services (SSIS) and Visual Studio explorer tools environments to get the connection properties of the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] and display them in the form of a GUI driven by the PropertyGrid.  
  
 To create a SiebelConnectionStringBuilder, use the following approach:  
  
```  
  
//In this example, factory is an instance of SiebelClientFactory  
SiebelConnectionStringBuilder bldr = (SiebelConnectionStringBuilder)factory.CreateConnectionStringBuilder();  
bldr.ConnectionString = connstr;  
```  
  
 Or, simply:  
  
```  
  
SiebelConnectionStringBuilder bldr = new SiebelConnectionStringBuilder();  
```  
  
 To see the keys and values supported as part of the `DbConnectionStringBuilder`, see [Data Provider properties for the Siebel Connection String](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).  
  
## See Also  
 [Extend ADO.NET Interfaces with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)
