---
description: "Learn more about: Configure a client binding for the SAP system"
title: "Configure a client binding for the SAP system"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configure a client binding for the SAP system
After you have generated the WCF client class, you can create a WCF client (instance) and invoke its methods to consume the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]. For information about how to generate the WCF client class and helper code for operations that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
 To create the WCF client, you must specify an endpoint address and a binding. The endpoint address must contain a valid SAP connection URI, and the binding must be an instance of an SAP Binding (**SAPBinding**). For more information about the SAP connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
 You can specify the SAP Binding and the endpoint address in your code or in a configuration file. When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the WCF client class, a configuration file (app.config) is also created for your project. This file contains configuration settings that reflect the binding properties and connection information (except credentials) that you specified when you connected to the SAP system with the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
## Specifying the Binding and Endpoint Address in Code  
 The following code shows how to create a WCF client by specifying the binding and endpoint address in code. It is good practice to specify the SAP system credentials by using the **ClientCredentials** property of the WCF client rather than in the connection URI supplied for the endpoint address.  
  
```  
// A WCF client that targets an RFC is created  
// by using a binding object and endpoint address  
SAPBinding sapBinding = new SAPBinding();  
EndpointAddress sapAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00");  
  
RfcClient rfcClient = new RfcClient(sapBinding, sapAddress);  
  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
rfcClient.Open();  
```  
  
## Specifying the Binding and Endpoint Address in a Configuration File  
 The following code shows how to create a WCF client by specifying the binding and endpoint address in an app.config file.  
  
```  
// A WCF client that targets an RFC is created  
// by specifying the client endpoint information in app.config  
RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
rfcClient.Open();  
```  
  
 The following XML shows the configuration file created for the EMP table by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. This file contains the client endpoint configuration referenced in the preceding example.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <sapBinding>  
                <binding name="SAPBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" receiveIdocFormat="Typed"  
                    generateFlatFileCompatibleIdocSchema="true" maxConnectionsPerSystem="50"  
                    enableConnectionPooling="true" idleConnectionTimeout="00:15:00"  
                    flatFileSegmentIndicator="SegmentDefinition" enablePerformanceCounters="false"  
                    autoConfirmSentIdocs="false"  
                    acceptCredentialsInUri="false" padReceivedIdocWithSpaces="false"  
                    enableBizTalkCompatibilityMode="false" />  
            </sapBinding>  
        </bindings>  
        <client>  
            <endpoint address="sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without"  
                binding="sapBinding" bindingConfiguration="SAPBinding" contract="Rfc"  
                name="SAPBinding_Rfc" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
 If a project has more than one WCF client, there will be multiple client endpoint entries defined in the configuration file. Each WCF client entry will have a unique name based on its binding configuration and target SAP system artifacts (such as Rfc and Trfc); for example, "SAPBinding_Rfc". If you connect multiple times to create the WCF clients in your project, multiple binding configuration entries will be created, one for each connection. These binding configuration entries will be named in the following manner: SAPBinding1, SAPBinding2, and so on. Each client endpoint entry created during a specific connection will reference the binding entry created during that connection.  
  
> [!IMPORTANT]
>  The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces different SAP artifacts of the same type (such as RFC, TRFC, and IDOC) as different operations of the same service contract. For example, two different RFCs, RFC_EXAMPLE_A and RFC_EXAMPLE_B, will both be surfaced under the same service contract ("Rfc"). This means that both RFCs will be invoked by the same WCF client class, **RfcClient**, and that the parameters for both RFCs will be declared in the same namespace. Therefore, you must generate the WCF client for both RFCs during the same [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] session (connection) to avoid experiencing a namespace collision when you build your solution.  
  
## See Also  
[Develop SAP applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)   
 [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)   
 [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)
