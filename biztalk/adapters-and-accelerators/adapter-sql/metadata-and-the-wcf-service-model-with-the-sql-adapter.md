---
description: "Learn more about: Metadata and the WCF Service Model with the SQL adapter"
title: "Metadata and the WCF Service Model with the SQL adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Metadata and the WCF Service Model with the SQL adapter
In the WCF service model, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutile.exe) to do the following:  
  
- Generate a service contract—the WCF service contract—through which your code can receive operations from the adapter. This .NET interface represents the service contract for target operations.  
  
- Generate proxy classes—the WCF client class—through which your code can invoke operations on the adapter.  
  
- Annotated classes that represent the supporting message contracts, operation contracts, and data contracts for the service contract.  
  
  For help in understanding the structure of this generated code, see [Understanding Generated Client Code](/dotnet/framework/wcf/feature-details/understanding-generated-client-code). This topic specifically describes code that svcutil.exe generates, but its content is also applicable to the code that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.  
  
  For information about how to generate a WCF client class or WCF service contract for target operations and about the differences between svcutil.exe and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
## See Also  
[Develop SQL applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)