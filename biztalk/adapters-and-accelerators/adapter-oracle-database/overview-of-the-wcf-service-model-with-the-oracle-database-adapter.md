---
title: "Overview of the WCF service model with the Oracle Database adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF service model, overview"
  - "invoking operations"
  - "WCF service, creating and implementing"
ms.assetid: 8ed765e5-b5e6-46bd-bcd6-282219caf75d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Overview of the WCF service model with the Oracle Database adapter
When you consume operations that the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces, your code acts either as a client or a service to the adapter. For almost all of the operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces, your code is the client. That is, your application invokes the operation on the adapter; for example to insert records into an Oracle table. The only operation for which your code acts as a service to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is for the POLLINGSMT operation. In this case, the adapter sends the results of the polling query operation to your application.  
  
 In the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] and WCF provide tools that enable you to generate this interface for targeted operations from the metadata that the adapter exposes. These tools also create a WCF client class that can be used to invoke the operations exposed in the service interface. A client application can call the methods of the WCF client class to invoke operations on the adapter. To implement a service to receive the POLLINGSTMT operation from the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you implement the interface generated for the POLLINGSTMT operation.  
  
 The following sections explain how to use the WCF service model to create client and service code for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
## Creating and Invoking Operations on a WCF Client by Using the Oracle Database Adapter  
 To use the WCF service model to invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must first generate a WCF client class for the target operations. You can then create an instance of this class, a WCF client, and call its methods to perform operations on the Oracle database.  
  
#### To invoke operations on the Oracle Database adapter  
  
1. Generate a WCF client class and helper code. Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class targeted at the Oracle database artifacts with which you want to work. For more information about how to generate a WCF client, see [Generating a WCF Client or a WCF Service Contract for Oracle Database Artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).  
  
2. Create a WCF client instance by specifying a client binding. Specifying a client binding involves specifying the binding and endpoint address that the WCF client will use. You can do this either imperatively in code or declaratively in configuration. For more information about how to specify a client binding, see [Configure a client binding for the Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-client-binding-for-the-oracle-database.md). The following code creates a WCF client that can be used to perform data manipulation language (DML) operations on an Oracle database table (/SCOTT/ACCOUNTACTIVITY). It also sets the credentials for the Oracle database. The WCF client is initialized from configuration.  
  
   ```  
   SCOTTTableACCOUNTACTIVITYClient aaTableClient =   
       new SCOTTTableACCOUNTACTIVITYClient("OracleDBBinding_SCOTT.Table.ACCOUNTACTIVITY");  
  
   aaTableClient.ClientCredentials.UserName.UserName = "SCOTT";  
   aaTableClient.ClientCredentials.UserName.Password = "TIGER";  
   ```  
  
3. Open the WCF client.  
  
   ```  
   aaTableClient.Open();  
   ```  
  
4. Invoke methods on the WCF client created in step 2 to perform operations on the Oracle database. The following code invokes the **Select** method of the WCF client to perform the following SQL SELECT query on the ACCOUNTACTIVITY table: `SELECT * FROM ACCOUNTACTIVITY`.  
  
   ```  
   // create a record set parameter to hold the SELECT query result set and invoke the Select operation;  
   microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] selectRecords;  
   selectRecords = aaTableClient.Select("*", null);  
   ```  
  
5. Close the WCF client.  
  
   ```  
   aaTableClient.Close();  
   ```  
  
   For more information about performing DML operations on tables and views, including the Select operation used above, see [Performing Basic Insert, Update, Delete, and Select Operations by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md).  
  
## Creating and Implementing a WCF Service by Using the Oracle Database Adapter  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] can perform polling on an Oracle database table or view. This functionality lets you specify a SQL SELECT query that the adapter should execute periodically against the Oracle database. The results of this query are returned to your application through a special operation, the POLLINGSTMT operation. To receive the results of the polling query, your application must implement the service contract that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes for the POLLINGSTMT operation.  
  
 To implement a service to receive the POLLINGSTMT operation, you must first generate the .NET interface (also called the WCF service contract) that represents the service contract exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] for the POLLINGSTMT operation. For more information about how to do this, see [Generating a WCF Client or a WCF Service Contract for Oracle Database Artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).  
  
 Then you implement a WCF service by implementing the generated interface. This class contains the business logic to process the POLLINGSTMT message and return a response to the adapter. Then you use a service host (**System.ServiceModel.ServiceHost**) to host an instance of this service. For more detailed information, see [Receiving Polling-based Data-changed Messages by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-service.md).  
  
## See Also  
 [Develop Oracle Database Applications by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)