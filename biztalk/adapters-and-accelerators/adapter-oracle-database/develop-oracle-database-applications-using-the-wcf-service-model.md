---
title: "Develop Oracle Database applications using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "performing operations, by using the WCF service model"
  - "developing applications, by using the WCF service model"
  - "WCF service model, using to develop applications"
ms.assetid: 3f2c60b2-4835-492d-8c3c-ed35d3e4c517
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop Oracle Database applications using the WCF Service Model
At the lowest level, the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] presents a programming model in which clients invoke operations on a service by exchanging SOAP messages over a channel established between client and service endpoints. This model, known as the WCF channel model, exposes data types and methods that enable you to operate directly on the WCF channel architecture. The WCF channel model provides you with direct control over the contents of the SOAP messages you create and over the way both your application and the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consume them; however, creating well-formed SOAP messages to send over a channel and validating the reply messages returned can be a detailed and exacting task.  
  
 For this reason, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides another programming model called the WCF service model. The WCF service model involves the use of proxy classes to invoke operations on a target service or to receive operations from a client.  
  
- The proxy class used to invoke operations on a target service is called a WCF client class. This class models the operations exposed by a service as .NET methods with strongly-typed parameters. By using the WCF service model, you can invoke the operations exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] as .NET methods on the WCF client. For more information about WCF clients, see "WCF Client Overview" at [http://go.microsoft.com/fwlink/?LinkId=91458](http://go.microsoft.com/fwlink/?LinkId=91458).  
  
- In the WCF service model, the service contract exposed by a service is represented by an interface. This managed code representation of the service contract is called a WCF service contract. The WCF service contract models operations as methods with strongly-typed parameters. To receive an operation from a client you implement a class, the WCF service, from this interface. You can then host an instance of this class in a **System.ServiceModel.ServiceHost** to enable a client to invoke the operation on your code. By using the WCF service model and a WCF service contract targeted to the POLLINGSTMT operation, you can receive the results of a polling operation on the Oracle database using [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
  You use tools to generate a WCF client class or a WCF service contract and associated helper code from the service metadata that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes. You can use either of the following tools:  
  
- The ServiceModel Metadata Utility Tool (svcutil.exe), which ships with WCF  
  
- The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], which ships with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]  
  
  The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] is integrated with the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] design experience and presents a standard Microsoft Windows interface that provides powerful browsing and searching capabilities on operations exposed by the adapter. For more information about how to generate a WCF client or a WCF service contract, see [Generate a WCF Client or a WCF Service Contract for Oracle Database Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).  
  
  Because it presents a model that is familiar to .NET programmers and that hides the underlying complexities of SOAP message exchange over a channel, the WCF service model is often the best choice to develop programming solutions for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. However, there are scenarios in which the WCF channel model might be a better choice. For example, the WCF service model only supports streaming for the ReadLOB operation. This is because serializing and de-serializing between the XML representation of objects in a SOAP message and the .NET types used to represent them in the service model involves reading the entire message into memory. (The result of a ReadLOB operation is an exception to this rule.)  
  
  The WCF channel model provides support for XML node-level streaming on all operations and data-level streaming on the ReadLOB and UpdateLOB operations. If you are dealing with queries that return large result sets or are attempting to update an LOB field in a table, the WCF channel model might be a better choice. For more information about using the WCF channel model, see [Develop Oracle Database Applications by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).  
  
  The topics in this section contain information, procedures, and examples to help you create and use the WCF service model to develop applications by using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
## In This Section  
  
-   [Overview of the WCF Service Model with the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md)  
  
-   [Metadata and the WCF Service Model with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/metadata-and-the-wcf-service-model-with-oracle-database.md)  
  
-   [Generate a WCF Client or a WCF Service Contract for Oracle Database Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)  
  
-   [Configure a Client Binding for the Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-client-binding-for-the-oracle-database.md)  
  
-   [Performing Basic Insert, Update, Delete, and Select Operations by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md)  
  
-   [Complete Operations on Tables with Large data types in Oracle Database by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-large-data-types-in-oracle-db-using-a-wcf-service.md)  
  
-   [Invoking Functions and Procedures in Oracle Database by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [Performing Operations Using REF CURSORS in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [Performing Operations Using RECORD Types in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [Performing a SQLEXECUTE Operation in Oracle Database by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [Receiving Polling-based Data-changed Messages in Oracle Database by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-service.md)  
  
-   [Receiving Oracle Database Change Notifications Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-the-wcf-service-model1.md)