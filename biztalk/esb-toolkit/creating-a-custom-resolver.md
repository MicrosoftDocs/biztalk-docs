---
title: "Creating a Custom Resolver | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2775460-8e04-40be-9557-8278336b031c
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating a Custom Resolver
The Resolver and Adapter Provider Framework implementation in [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses a pipeline component named Dispatcher and pipelines named ItineraryReceive and ItinerarySend.  
  
 The Dispatcher pipeline component has four properties: **Validate, Enabled, EndPoint,** and **MapName**. The **EndPoint** property can contain resolver connection strings with values such as the following, where **UDDI:\\\\** represents the resolution type to use (the root moniker).  
  
```  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=OrderPurchaseToOrderPost;serviceProvider=Microsoft.Practices.ESB  
```  
  
 Other supported monikers include **XPATH:\\\\, STATIC:\\\\,** and **BRE:\\\\**. Each moniker type uses a specific class that implements the **IResolveProvider** interface. You can create your own custom resolvers for other moniker types and register them for use by the dynamic resolution system.  
  
 The moniker equates to a resolver connection string. Individual schemas define the parameters and their root moniker. A resolver takes the resolver connection string, validates it, and uses the result to query and populate a **Dictionary** object that can be used for routing, transformation, itinerary selection, or some other purpose specific to your service.  
  
## Resolver Configuration  
 You must register all resolvers in the Esb.config configuration file. The following XML shows an example of the configuration file content.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
     <configSections>  
          <section name="esb" type="Microsoft.Practices.ESB.Configuration.ESBConfigurationSection, Microsoft.Practices.ESB.Configuration, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
          <!-- Other Section Definitions Here -->  
     </configSections>  
  
     <esb>  
          <resolvers cacheManager= "Resolver Providers Cache Manager"  absoluteExpiration="3600">  
               <resolver name="UDDI" type="Microsoft.Practices.ESB.Resolver.UDDI.ResolveProvider, Microsoft.Practices.ESB.Resolver.UDDI, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22">  
                    <resolverConfig>  
                         <add name="cacheTimeoutValue" value="120" />  
                         <add name="cacheName" value="UDDI Cache Manager" />  
                    </resolverConfig>  
               </resolver>  
               <resolver name="XPATH" type="Microsoft.Practices.ESB.Resolver.XPATH.ResolveProvider, Microsoft.Practices.ESB.Resolver.XPATH, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
               <!-- Other Resolver Definitions Here -->  
          </resolvers>  
          <!-- Other ESB Configuration Settings Here -->  
     </esb>  
     <!-- Other Configuration Sections Here -->  
</configuration>  
```  
  
 The **resolverConfig** section under each resolver node allows you to configure additional properties that your resolver may require to operate in a specific environment. To have access to the configuration, your resolver must expose a constructor that takes in a parameter of type **Microsoft.Practices.ESB.Configuration.Resolver**. In your resolver implementation, configuration properties can then be accessed using the **ReadResolverConfigByKey** method of the **ResolverConfigHelper** class; to do this, pass in the parameter originally passed to the constructor, and then pass in the name of the value in question. If no name-value pairs are specified in the **resolverConfig** node, the default parameterless constructor will be used to instantiate your resolver.  
  
 Two Universal Description, Discovery, and Integration (UDDI) 3 resolvers have been defined in the configuration: UDDI 3 and UDDI 3-SOASOFTWARE. Both of these resolvers use the same underlying assembly, but they provide different configurations for supporting different UDDI 3.0–compliant registries with different Uniform Resource Identifier (URI) formats and security requirements. If you need to configure an additional moniker for a UDDI 3.0–compliant registry besides those already supported, the following configuration properties can be used:  
  
- **cacheTimeoutValue**  
  
- **cacheName**  
  
- **publisherKey**  
  
- **useUddiAuth**  
  
- **baseUri**  
  
- **inquireUriSuffix**  
  
- **securityUriSuffix**  
  
- **securityMode**. For valid values, see the enumeration [System.ServiceModel.BasicHttpSecurityMode](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409) ([http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409)). The default value is **TransportCredentialOnly**.  
  
- **credentialType**. For valid values, see the enumeration [System.ServiceModel.HttpClientCredentialType](http://go.microsoft.com/fwlink/?LinkId=188285) ([http://go.microsoft.com/fwlink/?LinkId=188285](http://go.microsoft.com/fwlink/?LinkId=188285)). The default value is **Windows**.  
  
- **username**  
  
- **password**  
  
  If you want to create a resolver that relies on the dependency injection capabilities of the Unity Application Block, additional configuration is required. For more information, see [Creating a Custom Resolver with a Unity Container](../esb-toolkit/creating-a-custom-resolver-with-a-unity-container.md).  
  
## The IResolveProvider Interface  
 All resolvers must implement the **IResolveProvider** interface. The **IResolveProvider** interface, located in the Microsoft.Practices.ESB.Resolver project, consists of three overloads of the **Resolve** method that return an instance of the **Dictionary** class, which contains resolution facts provided by the instance of concrete resolver class. The following code example shows the signature of these method overloads.  
  
```csharp  
// <summary>  
// This is the main interface that is called from the   
// ResolverMgr class.  
// This interface supports being called from a Microsoft BizTalk   
// Server pipeline component.  
// </summary>  
// <param name="config">Configuration string entered into   
// pipeline component as argument</param>  
// <param name="resolver">Moniker representing the resolver   
// to load</param>.  
// <param name="message">IBaseMessage passed from pipeline</param>.  
// <param name="pipelineContext">IPipelineContext passed from   
// pipeline</param>.  
// <returns>Dictionary object fully populated</returns>.  
        Dictionary<string, string> Resolve(string config, string resolver,  
              IBaseMessage message, IPipelineContext pipelineContext);  
  
// <summary>  
// This is the main interface that is called from the ResolverMgr   
// class.  
// This interface supports being called from a Web service interface.  
// </summary>  
// <param name="config">Configuration string entered into Web   
// service as argument</param>.  
// <param name="resolver">Moniker representing the resolver   
// to load</param>.  
// <param name="message">XML document passed from Web   
// service</param>.  
// <returns>Dictionary object fully populated</returns>.  
        Dictionary<string,string> Resolve(string config, string resolver, System.Xml.XmlDocument message);  
  
// <summary>  
// This is the main interface that is called from the   
// ResolverMgr class.  
// This interface supports being called from an orchestration.  
// </summary>  
// <param name="resolverInfo">Configuration string containing   
// configuration and resolver</param>.  
// <param name="message">XLANGMessage passed from   
// orchestration</param>.  
// <returns>Dictionary object fully populated</returns>.  
        Dictionary<string, string> Resolve(ResolverInfo resolverInfo, XLANGs.BaseTypes.XLANGMessage message);  
```  
  
 The **Resolution** structure, located in Microsoft.Practices.ESB.Resolver project, also defines the name/value pairs stored in the **Dictionary** instance. The **Resolution** structure exposes several properties; the following table lists the most relevant of these. The **CreateResolverDictionary** method of the **ResolutionHelper** class can be used to generate a resolver dictionary that contains the most used keys, with empty string values. The **Dictionary** instance supports the addition of custom resolver name/value pairs through a concrete implementation of the **Resolver** class.  
  
|Property|Data type|Data type|Data type|  
|--------------|---------------|---------------|---------------|  
|**TransformType**|String|**ActionField**|String|  
|**Success**|Boolean|**EpmRRCorrelationTokenField**|String|  
|**TransportNamespace**|String|**InboundTransportLocationField**|String|  
|**TransportType**|String|**InterchangeIDField**|String|  
|**TransportLocation**|String|**ReceiveLocationNameField**|String|  
|**Action**|String|**ReceivePortNameField**|String|  
|**MessageExchangePattern**|String|**InboundTransportTypeField**|String|  
|**EndpointConfig**|String|**IsRequestResponseField**|String|  
|**TargetNamespace**|String|**DocumentSpecStrongNameField**|String|  
|**FixJaxRPC**|Boolean|**DocumentSpecNameField**|String|  
|**WindowUserField**|String|**MessageType**|String|  
|**CacheTimeout**|String|**OutboundTransportCLSID**|String|  
|**MethodNameField**|String|||  
  
## Creating a Custom Resolver  
 At run time, a pipeline retrieves the resolver connection string and calls the resolver manager (an instance of the **ResolverMgr** class). The resolver manager parses, populates, and validates the resolver connection string. It does this by doing the following:  
  
- It parses the connection string to determine which **Resolver** type to load.  
  
- It matches this type to a moniker defined in the configuration file (the key is the root moniker, such as UDDI).  
  
- It reads the assembly name of the resolver for this moniker.  
  
- It loads the specified assembly.  
  
  The dynamic resolution mechanism caches all loaded implementations of the **IResolveProvider** interface to avoid repeated reading of configuration information and assembly loading when several incoming messages use the same resolver.  
  
  Finally, the resolver manager executes the **Resolve** method of the concrete **IResolveProvider** implementation and returns the populated **Dictionary** instance.  
  
  **To create a custom resolver**  
  
1.  Create an assembly with a class that implements the **IResolveProvider** interface and contains a **Resolve** method that returns resolver facts as an instance of the **Dictionary** class.  
  
2.  Register the resolver by adding it to the Esb.config configuration file using a **\<resolver\>** element that contains the root moniker as the **name** attribute and the fully qualified assembly name as the **type** attribute.  
  
3.  (Optional) Create a schema that defines the root moniker and the query parameters, and then save it in the ESB.Schemas.Resolvers folder. The name should follow existing ESB naming conventions; this means it should use the name of the root moniker appended with "_Resolution.xsd".  
  
4.  (Optional) Generate a class from the new schema and save it in the custom resolver assembly. This exposes typed parameters in the custom resolver.  
  
5.  Register the new assembly in the global assembly cache.