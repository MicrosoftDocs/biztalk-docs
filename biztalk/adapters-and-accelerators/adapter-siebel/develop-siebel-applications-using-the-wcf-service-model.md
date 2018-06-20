---
title: "Develop Siebel applications using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF service model, developing applications by using"
  - "WCF service model, performing operations"
  - "proxy programming, performing operations"
  - "WCF service model, advantages of using"
ms.assetid: df5627b9-c80d-4a75-a20a-a0be119735a2
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop Siebel applications using the WCF Service Model
[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides a programming model called the WCF service model, which, in part, helps address some of the limitations of another programming model—the WCF channel model.  
  
 At the lowest level, the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] presents the WCF channel model in which clients invoke operations on a service by exchanging SOAP messages over a channel established between client and service endpoints. The WCF channel model exposes data types and methods that enable you to operate directly on the WCF channel architecture. The WCF channel model provides you with direct control over the contents of the SOAP messages you create and over the way both your application and the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] consume them. However, creating well-formed SOAP messages to send over a channel and validating the reply messages returned can be a detailed and exacting task.  
  
 The WCF service model, however, involves the use of proxy classes to invoke operations on a target service or to receive operations from a client. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposes the Siebel system as a WCF service on which you can invoke operations.  
  
- The proxy class used to invoke operations on a target service is called a WCF client class. This class models the operations exposed by a service as .NET methods with strongly-typed parameters. By using the WCF service model, you can invoke the operations exposed by the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] as .NET methods on the WCF client. For more information about WCF clients, see [WCF Client Overview](https://msdn.microsoft.com/library/ms735103.aspx).   
  
  You use tools to generate a WCF client class and associated helper code from the service metadata that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposes. You can use either of the following tools:  
  
- The ServiceModel Metadata Utility Tool (svcutil.exe), which ships with WCF  
  
- The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], which ships with the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]  
  
  The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] is integrated with the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] design experience and presents a standard Microsoft Windows interface that provides powerful browsing and searching capabilities on operations exposed by the adapter. For more information about how to generate a WCF client, see [Generate a WCF Client or a WCF service contract for Siebel solution Artifacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)  
  
## Why Choose the WCF Service Model or the WCF Channel Model?  
 Because it presents a model that is familiar to .NET programmers and hides the underlying complexities of SOAP message exchange over a channel, the WCF service model is often the best choice to develop programming solutions for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. However, there are scenarios in which the WCF channel model might be a better choice. For example, serializing and de-serializing between the XML representation of objects in a SOAP message and the .NET types used to represent them in the WCF service model involves reading the entire message into memory.  
  
 The WCF channel model provides support for XML node-level streaming on all operations. In node-level streaming, only each node of the XML message is held in memory at any one time. For certain operations, for example, if you are performing queries that return large result sets, the WCF channel model might be a better choice for your application. For more information about using the WCF channel model, see [Develop Siebel Applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md).  
  
 The topics in this section contain information, procedures, and examples to help you create and use the WCF service model to develop applications by using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
## In This Section  
  
-   [Overview of the WCF Service Model with the Siebel Adapter](../../adapters-and-accelerators/adapter-siebel/overview-of-the-wcf-service-model-with-the-siebel-adapter.md)  
  
-   [Metadata and the WCF Service Model with Siebel](../../adapters-and-accelerators/adapter-siebel/metadata-and-the-wcf-service-model-with-siebel.md)  
  
-   [Generate a WCF Client or a WCF service contract for Siebel solution Artifacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)  
  
-   [Configure a WCF Client for a Siebel System](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)  
  
-   [Run Operations on Business Components with the Siebel adapter using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)  
  
-   [Run Operations on Business Components with MVG Fields with the Siebel adapter using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md)  
  
-   [Invoke Business Service Methods with the Siebel adapter using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/run-business-service-methods-with-the-siebel-adapter-using-a-wcf-service.md)  
  
## See Also  
[Develop your Siebel applications](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)