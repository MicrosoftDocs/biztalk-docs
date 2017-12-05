---
title: "Examining the Core Interface for a Managed Provider2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53cdb352-5532-4e0a-bfb3-1901e796d96c
caps.latest.revision: 3
---
# Examining the Core Interface for a Managed Provider
A data provider in the .NET Framework serves as a bridge between an application and a data source. The data provider is used to retrieve data from a data source and to reconcile changes to that data back to the data source.  
  
 ADO.NET exposes a common model for .NET Framework data provider objects so that a single set of code can be written to work regardless of the .NET Framework data provider. The `Connection`, `Command`, `DataReader`, and `DataAdapter` objects represent the core elements of the .NET Framework data provider model. The following table describes the purpose of these objects, and how they are implemented in the Managed Provider for DB2 and Managed Provider for Host Files.  
  
|Common model|Managed Provider for Host Integration Server|Description|  
|------------------|--------------------------------------------------|-----------------|  
|Connection|<xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Connection><br /><br /> <xref:Microsoft.HostIntegration.MsHostFileClient.HostFileConnection>|Responsible for opening, closing, and maintaining a connection to a DB2 host.|  
|Command|<xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command><br /><br /> <xref:Microsoft.HostIntegration.MsHostFileClient.HostFileCommand>|Manages all parameters that a query may include, which includes both SQL parameters and stored procedure parameters.|  
|DataReader|<xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader>|A server-side forward-only cursor implementation that inherits form the `IDataReader` and `IDataRecord` interfaces.|  
|DataAdapter|<xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataAdapter><br /><br /> <xref:Microsoft.HostIntegration.MsHostFileClient.HostFileDataAdapter>|Acts as the gateway between the host data and a .NET Framework data set.|  
  
 In addition, each provider has several interfaces specific to this implementation. These interfaces deal with exception and event handling, setting up connections to a DB2 host over different types of networks, and passing parameters.  
  
## See Also  
 [.NET Framework Data Providers for Host Integration Server](../HIS2010/net-framework-data-providers-for-host-integration-server2.md)   
 [Managed Provider Programmer's Guide](../HIS2010/managed-provider-programmer-s-guide1.md)