---
title: "Overview of the WCF service model with the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF service model, overview of using"
ms.assetid: 02a4b43e-ade0-4dba-b8f6-074bca7cbe5c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Overview of the WCF service model with the SAP adapter
When you consume operations that the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces, your code acts either as a client or a service to the adapter.  
  
 Your code acts as a client to invoke the following kinds of operations on the SAP system:  
  
- Invoke a Remote Function Call (RFC).  
  
- Invoke a Transactional Remote Function Call (tRFC).  
  
- Invoke a Business Application Programming Interface (BAPI).  
  
- Send an Intermediate Document (IDOC)  
  
  Your code acts as a service to receive the following kinds of operations:  
  
- Receive an RFC (RFC server)  
  
- Receive a tRFC (tRFC server)  
  
- Receive an IDOC.  
  
> [!NOTE]
>  Because BAPIs are methods exposed by the SAP system on business objects located in the Business Object Repository (BOR), you cannot receive BAPIs.  
  
 In the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] and WCF provide tools that enable you to generate this interface for targeted operations from the metadata that the adapter exposes. These tools also create a WCF client class that can be used to invoke the operations exposed in the service interface. A client application can call the methods of the WCF client class to invoke operations on the adapter. To implement a service to receive operations from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you implement the interface generated for the target operation.  
  
 The following sections explain how to use the WCF service model to create client and service code for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## Creating a WCF Client and Invoking Operations on SAP  
 To use the WCF service model to invoke operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must first generate a WCF client class for the target operations. You can then create an instance of this class, a WCF client, and call its methods to perform operations on the SAP system.  
  
#### To invoke operations on the SAP adapter  
  
1. Generate a WCF client class and helper code. Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class targeted at the SAP system artifacts with which you want to work. For more information about how to generate a WCF client, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
2. Create a WCF client instance by specifying a client binding. Specifying a client binding involves specifying the binding and endpoint address that the WCF client will use. You can do this either imperatively in code or declaratively in configuration. For more information about how to specify a client binding, see [Configure a client binding for the SAP system](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md). The following code creates a WCF client that can be used to invoke an RFC on the SAP system. It also sets the credentials for the SAP system. The WCF client is initialized from configuration.  
  
   ```  
   RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
   rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
   rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
   ```  
  
3. Open the WCF client.  
  
   ```  
   rfcClient.Open();  
   ```  
  
4. Invoke methods on the WCF client created in step 2 to perform operations on the SAP system. The following code invokes the **SD_RFC_CUSTOMER_GET** method of the WCF client to invoke the RFC on the SAP system.  
  
   ```  
   microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers =   
       new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
   rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
   ```  
  
5. Close the WCF client.  
  
   ```  
   rfcClient.Close();  
  
   ```  
  
## Creating and Implementing a WCF Service by Using the SAP Adapter  
 To use the WCF service model to receive operations from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must first generate the .NET interface (also called the WCF service contract) that represents the service contract exposed by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] for the operation. For more information about how to do this, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
 You then implement a WCF service by implementing the generated interface. This class contains the business logic to process the operation and return a response to the adapter. Then you use a service host (**System.ServiceModel.ServiceHost**) to host an instance of this service.  
  
#### To create and implement a WCF service  
  
1. Generate a WCF service contract and helper classes. Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or svcutil.exe to generate a WCF service contract (interface) targeted at the SAP system artifacts with which you want to work. For more information about how to generate a WCF client, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
2. Implement a WCF service from the interface and helper classes generated in step 1. If an error is encountered processing the data for the operation, the method that handles that operation can throw an exception to return a fault to the SAP system; otherwise the method must return an instance of the appropriate (generated) response class for the operation. You must attribute the WCF service class as follows:  
  
   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
   ```  
  
   1. If you used the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate the interface, you can implement your logic directly in the appropriate method in the generated **SAPBindingService** class. This class can be found in SAPBindingService.cs. The following code sub-classes the **SAPBindingService** class.  
  
      ```  
      [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single,UseSynchronizationContext = false)]  
      class RfcServerClass : SAPBindingNamespace.SAPBindingService  
      {  
          public override Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request)  
          {  
              // If either parameter is null throw an exception   
              if (request.X == null || request.Y == null)  
                  throw new System.ArgumentNullException();  
  
              // Add the two operands  
              int result = (int) (request.X + request.Y);  
  
              return new Z_RFC_MKD_ADDResponse(result);  
          }  
      }  
      ```  
  
   2. If you used svcutil.exe to generate the interface, you must create a class that implements the interface and implement your logic in the appropriatemethod of this class.  
  
3. Create an instance of the WCF service created in step 2.  
  
   ```  
   // create service instance  
   RfcServerClass rfcServerInstance = new RfcServerClass();  
   ```  
  
4. Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI. The base connection URI cannot contain userinfoparams or a query_string.  
  
   ```  
   // Enable service host  
   Uri[] baseUri = new Uri[] { new Uri("sap://a/YourSAPHost/00") };  
   ServiceHost srvHost = new ServiceHost(pollingInstance, baseUri);  
   ```  
  
5. Create an **SAPBinding** and configure it for the operation by setting its binding properties. You can do this either explicitly in code or declaratively in configuration. At a minimum, you must set **AcceptCredentialsInUri** to **true**.  
  
   ```  
   // Create and configure a binding for the service endpoint. NOTE: binding  
   // parameters are set here for clarity, but these are already set in the  
   // the generated configuration file  
   SAPBinding binding = new SAPBinding();  
  
   // The credentials are included in the connection URI, so set this property to true  
   binding.AcceptCredentialsInUri = true;  
   ```  
  
6. Add a service endpoint to the service host. To do this:  
  
   -   Use the binding created in step 5.  
  
   -   Specify a connection URI that contains credentials and specifies a listener connection (SAP gateway, gateway service and program ID) in the query_string. For more information about the SAP connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
   -   Specify the service contract. This is the name of the interface that represents the WCF service contract. For RFCs, it is "Rfc".  
  
   ```  
   // Add service endpoint   
   // NOTE: The contract for the service endpoint is "Rfc".  
   //       This is the generated WCF service contract (interface) -- see SAPBindingInterface.cs.  
   Uri serviceUri = new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGW00&ListenerGwHost=YourSapHost&ListenerProgramId=SAPAdapter");  
   srvHost.AddServiceEndpoint("Rfc", binding, serviceUri);  
   ```  
  
7. To receive the operation from the SAP system, open the service host. Your WCF service will be invoked whenever the SAP system invokes the operation on the program ID and system specified in the service URI in step 6.  
  
   ```  
   // Open the service host to begin receiving the operation.  
   srvHost.Open();  
   ```  
  
8. To stop receiving the operation, close the service host.  
  
   > [!IMPORTANT]
   >  The adapter will continue to receive the operation until the service host is closed. You should always close the service host when you no longer want to receive the operation.  
  
   ```  
   srvHost.Close();  
   ```  
  
## See Also  
[Develop SAP applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)