---
description: "Learn more about: Configure a WCF Client for a Siebel System"
title: "Configure a WCF Client for a Siebel System"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configure a WCF Client for a Siebel System
After you have generated the WCF client class, you can create a WCF client (instance) and invoke its methods to consume the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. For information about how to generate the WCF client class and helper code for operations that the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] exposes, see [Generate a WCF Client or a WCF service contract for Siebel solution Artifacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).  
  
 To create the WCF client, you must specify an endpoint address and a binding. The endpoint address must contain a valid Siebel connection URI, and the binding must be an instance of a Siebel Binding (**SiebelBinding**). For more information about the Siebel connection URI, see [Connect to the Siebel System in Visual Studio](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md).  
  
 You can specify the Siebel Binding and the endpoint address in your code or in a configuration file. When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the WCF client class, a configuration file (app.config) is also created for your project. This file contains configuration settings that reflect the binding properties and connection information (except credentials) that you specified when you connected to the Siebel system with the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
## Specifying the Binding and Endpoint Address in Code  
 The following code shows how to create a WCF client by specifying the binding and endpoint address in code. It is good practice to specify the Siebel credentials by using the **ClientCredentials** property of the WCF client rather than in the connection URI supplied for the endpoint address.  
  
```  
// A WCF client that targets the TimeStamp business service is created  
// by using a binding object and endpoint address  
SiebelBinding sblBinding = new SiebelBinding();  
EndpointAddress sblAddress = new EndpointAddress("siebel://Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=ent_server&Language=enu");  
  
BusinessServices_TimeStamp_OperationClient client =   
    new BusinessServices_TimeStamp_OperationClient(sblBinding, sblAddress);  
  
    client.ClientCredentials.UserName.UserName = "SADMIN";  
    client.ClientCredentials.UserName.Password = "SADMIN";  
  
    client.Open();  
```  
  
## Specifying the Binding and Endpoint Address in a Configuration File  
 The following code shows how to create a WCF client by specifying the binding and endpoint address in an app.config file.  
  
```  
// A WCF client that targets the TimeStamp business service is created  
// by specifying the client endpoint information in app.config  
BusinessServices_TimeStamp_OperationClient client =   
    new BusinessServices_TimeStamp_OperationClient("SiebelBinding_BusinessServices_TimeStamp_Operation");  
  
client.ClientCredentials.UserName.UserName = "SADMIN";  
client.ClientCredentials.UserName.Password = "SADMIN";  
  
client.Open();  
```  
  
### The App.config File  
 The following XML shows the configuration file created for the TimeStamp business service by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. This file contains the client endpoint configuration referenced in the preceding example.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <siebelBinding>  
                <binding name="SiebelBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" enableBizTalkCompatibilityMode="false"  
                    enablePerformanceCounters="false" enableConnectionPooling="true"  
                    maxConnectionsPerSystem="5" idleConnectionTimeout="00:01:00"  
                    acceptCredentialsInUri="false" />  
            </siebelBinding>  
        </bindings>  
        <client>  
            <endpoint address="siebel://Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=ent_server&Language=enu"  
                binding="siebelBinding" bindingConfiguration="SiebelBinding"  
                contract="BusinessServices_TimeStamp_Operation" name="SiebelBinding_BusinessServices_TimeStamp_Operation" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
 If a project has more than one WCF client, there will be multiple client endpoint entries defined in the configuration file. Each WCF client entry will have a unique name based on its binding configuration and target Siebel artifact; for example, " SiebelBinding_BusinessServices_TimeStamp_Operation ". If you connect multiple times to create the WCF clients in your project, multiple binding configuration entries will be created, one for each connection. These binding configuration entries will be named in the following manner: SiebelBinding, SiebelBinding1, SiebelBinding2, and so on. Each client endpoint entry created during a specific connection will reference the binding entry created during that connection.  
  
## See Also  
 [Develop Siebel Applications using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)
