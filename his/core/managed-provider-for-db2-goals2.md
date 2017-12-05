---
title: "Managed Provider for DB2 Goals2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28f25d33-0318-43f4-b35a-caa412c12722
caps.latest.revision: 5
---
# Managed Provider for DB2 Goals
The main goal of the Managed Provider for DB2 is to enable access to loosely coupled data sources using the technologies offered by ADO.NET and the .NET Framework. To implement this goal, the Managed Provider for DB2 was designed as an incremental improvement over the traditional COM-based OLE DB providers. In addition, the Managed Provider for DB2 is optimized for DB2 over the currently available OLE DB .NET Framework data provider.  
  
## OLE DB Solutions  
 Microsoft has offered programming models and tools for developing enterprise data integration solutions for several years, one of which includes the COM-based OLE DB. However, developing and deploying ADO-based Web solutions presents a number of issues, including insufficient design tools, decreased performance, limited scalability, and little XML interoperability.  
  
 Additionally, the ADO- and OLE DB-based data architecture is based on solutions that require tightly coupled, live connections between application and data tiers. However, the vast majority of Web solutions today require a loosely coupled association between application components and tiers. Also, most modern Web application requirements include the use of XML as the universal Web message and data medium. Remote Data Services (RDS) offered a disconnected recordset between application and presentation tiers. ADO also offered the ability to persist recordsets as XML. However, there was no uniform way to provide asynchronous execution between tiers. In addition, XML recordset persistence was extremely limited.  
  
## ADO.NET and the .NET Framework  
 To make implementation easier and to improve performance, scalability, and XML support, Microsoft offered the .NET Framework and ADO.NET. The .NET Framework offered developers a number of advantages over COM, such as cross-language inheritance, object lifetime management, and multilanguage class libraries as supported by the common language runtime (CLR). The CLR offers developers a predictable, managed environment in which to execute their programs. The ADO.NET programming model was designed to provide better performance and scalability than the older ADO. ADO.NET is a set of common classes for exposing data services that are implemented by .NET Framework data providers.  
  
 Microsoft Visual Studio has shipped two .NET Framework data provider implementations: the first provider accesses Microsoft SQL Server through an application-level protocol called Tabular Data Stream (TDS), and is called the SQL Server .NET Framework Data Provider. The second provider accesses the underlying OLE DB providers, and is called the OLE DB .NET Framework Data Provider.  
  
 The OLE DB .NET Framework Data Provider adds complexity and compatibility issues with an extra layer of indirection. Therefore, Host Integration Server has implemented a .NET Framework data provider for a key enterprise data source: DB2.  
  
## See Also  
 [Managed Provider for DB2 Programmer's Guide](../core/managed-provider-for-db2-programmer-s-guide1.md)