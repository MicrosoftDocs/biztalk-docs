---
title: "Overview of the WCF service model with the Oracle E-Business Suite adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aeeac8a4-a4bc-4963-951c-0c806e232f1e
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Overview of the WCF service model with the Oracle E-Business Suite adapter
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes an Oracle E-Business Suite system as a WCF service. To perform operations on Oracle E-Business Suite artifacts, for example to invoke a stored procedure, you invoke an operation on the adapter, which, in turn, performs the operation on the Oracle E-Business Suite. Your code acts as a client to the WCF service presented by the adapter.  
  
 In the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] and WCF provide tools that enable you to generate this interface for targeted operations from the metadata that the adapter exposes. These tools also create a WCF client class that can be used to invoke the operations exposed in the service interface. A client application can call the methods of the WCF client class to invoke operations on the adapter.  
  
 The following section explains how to use the WCF service model to invoke operations with a WCF client.  
  
## Invoking Operations on the Oracle E-Business Suite with a WCF Client  
 To use the WCF service model to invoke operations on the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must first generate a WCF client class for the target operations. You can then create an instance of this class, a WCF client, and call its methods to perform these operations on the Oracle E-Business Suite.  
  
#### To invoke operations on the Oracle E-Business adapter  
  
1. Generate a WCF client class and helper code. Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class targeted at Oracle E-Business Suite artifacts with which you want to work. For more information about how to generate a WCF client, see [Generate a WCF Client or a WCF Service Contract for Oracle E-Business Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).  
  
2. Create a WCF client instance and configure the WCF client. Configuring the WCF client involves specifying the binding and endpoint address (connection URI) that the client will use. You can do this either imperatively in code or declaratively in configuration. The following code creates a WCF client that targets the **Customer Interface** concurrent program in the **Receivables** application in the Oracle E-Business Suite. It also sets the credentials for the Oracle E-Business Suite. The WCF client is initialized from configuration.  
  
   ```  
   ConcurrentPrograms_ARClient client = new ConcurrentPrograms_ARClient("OracleEBSBinding_ConcurrentPrograms_AR"); //picking the binding and address from app.config  
  
   client.ClientCredentials.UserName.UserName = "myuser";  
   client.ClientCredentials.UserName.Password = "mypassword";  
   ```  
  
   > [!NOTE]
   >  You can either specify the client binding and endpoint address in the code or declare it in the app.config configuration file. The preceding code snippet uses the latter. For more information on how to use either approaches, see [Configure a Client Binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).  
  
3. Open the WCF client.  
  
   ```  
   client.Open();  
   ```  
  
4. Invoke methods on the WCF client created in step 2 to perform operations on the Oracle E-Business Suite. The following code invokes the **Customer Interface** concurrent program in the **Receivables** application in the Oracle E-Business Suite.  
  
   ```  
   string Result = client.RACUST(null, null, null, description, null, recipro_cust, org_id);  
   ```  
  
    **RACUST** is the actual name of the Customer Interface concurrent program. **Customer Interface** is the friendly name of the concurrent program.  
  
5. Close the WCF client.  
  
   ```  
   client.Close();  
   ```  
  
## See Also  
 [Develop Oracle E-Business Suite Applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)