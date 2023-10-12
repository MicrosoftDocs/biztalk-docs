---
description: "Learn more about: Metadata and the WCF Service Model with Siebel"
title: "Metadata and the WCF Service Model with Siebel"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Metadata and the WCF Service Model with Siebel
In the WCF service model, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutile.exe) to generate a proxy class—the WCF client class—through which your code can invoke operations on the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].

 These tools use the metadata exposed by the adapter to generate:

- An annotated .NET interface that represents the service contract for target operations. This interface is called the WCF service contract.

- Annotated classes that represent the supporting message contracts, operation contracts, and data contracts for the service contract.

- A WCF client class whose methods can be used to invoke the service methods (operations) exposed by the WCF service contract.

  For help in understanding the structure of this generated code, see "Understanding Generated Client Code" at [https://go.microsoft.com/fwlink/?LinkId=98365](/dotnet/framework/wcf/feature-details/understanding-generated-client-code). This topic specifically describes code that svcutil.exe generates, but its content is also applicable to the code that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.

  For information about how to generate a WCF client class for target operations and about the differences between svcutil.exe and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF Client or a WCF service contract for Siebel solution Artifacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)

## See Also
 [Develop Siebel applications using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)