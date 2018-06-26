---
title: "ESB Resolver and Adapter Provider Framework | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb7ea42e-b32c-40a8-b36b-c349f56f6edd
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Resolver and Adapter Provider Framework
The Resolver and Adapter Provider Framework supports itinerary, transformation, and endpoint resolution and routing. The framework can dynamically resolve endpoints and set outbound adapter properties. After a resolver component resolves an endpoint (for example, using Universal Description, Discovery, and Integration [UDDI] to look up an outbound Web service endpoint), an adapter provider component sets specific properties of registered BizTalk Server adapters. For example, the WCF-BasicHttp adapter provider is responsible for setting the BizTalk-specific message context properties for the endpoint URI that will use the specific BizTalk adapter; the FTP adapter provider is responsible for setting the properties specific to the FTP adapter.  
  
 One goal of the Resolver and Adapter Provider Framework is to support resolution and routing at either the messaging level, without requiring the use of BizTalk orchestrations, or at the orchestration level. In both cases, the pluggable framework provides easy development, deployment, and registration of new resolvers and adapter providers. All resolvers and adapter providers implement well-defined interfaces and are demand-loaded at run time through registration in the configuration files.  
  
 Both the ESB Dispatcher and ESB Dispatcher Disassemble pipeline components use the Resolver and Adapter Provider Framework by passing the connection string from either the itinerary SOAP header or the pipeline configuration to the Resolver Manager.  
  
 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] configuration contains details of all registered resolvers and adapter providers. At run time, the resolver managers and adapter managers read details of the registered resolvers and adapter providers from the configuration files, load the appropriate assemblies, and store them in a BizTalk host–level cache. This caching technique removes the requirement for repeated reading of configuration files and loading of assemblies for every submitted message.  
  
 For more information about how the Resolver and Adapter Provider Framework works and how you can extend it by creating custom resolvers and adapter providers, see [Modifying and Extending the BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).  
  
## Supported Resolution Mechanisms (Resolvers)  
 The BizTalk ESB Toolkit includes the following resolvers: **STATIC, UDDI, UDDI3, XPATH, BRE, BRI, ITINERARY, ITINERARY-STATIC** and **LDAP**.  
  
 A resolver's connection string always consists of a **moniker** (such as **BRE**) followed by ":\\\\" and the connection or processing details. The moniker matches the definition of the associated resolver in the configuration file. The properties associated with each connection string are unique, and not all properties are required. The schema for each of the resolvers can be found in the ESB.Resolvers.Schemas project.  
  
 The following are examples of connection strings:  
  
- **STATIC**  
  
   STATIC:\\\TransportType=;  
  
   TransportLocation=<http://localhost/ESB.CanadianServices/SubmitPOService.asmx>;  
  
   Action=;  
  
   EndPointConfig=;  
  
   JaxRpcResponse=false;  
  
   MessageExchangePattern=;  
  
   TargetNamespace=<http://globalbank.esb.dynamicresolution.com/canadianservices/>;  
  
   TransformType=;  
  
- **UDDI**  
  
   UDDI:\\\serverUrl=<http://localhost:9901/rmengine>;  
  
   serviceName=OrderPurchaseWebService;  
  
   serviceProvider=Microsoft Practices ESB  
  
- **XPATH**  
  
   XPATH:\\\TransportType=;  
  
   `TransportLocation=/*[local-name()='OrderDoc' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*[local-name()='ID' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];`  
  
   Action=;  
  
   EndPointConfig=;  
  
   JaxRpcResponse=;  
  
   MessageExchangePattern=;  
  
   `TargetNamespace=/*[local-name()='OrderDoc' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*[local-name()='customerName' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];`  
  
   TransformType=;  

- **BRE**  
  
   BRE:\\\policy=GetCanadaEndPoint;  
  
   version=;  
  
   useMsg=;  
  
- **BRI**  
  
   BRI:\\\policy=ResolveItinerary;  
  
   version=;  
  
   useMsg=;  
  
- **ITINERARY**  
  
   ITINERARY:\\\name=TwoWayTestItinerary;  
  
   version=;  
  
- **ITINERARY-STATIC**  
  
   ITINERARY-STATIC:\\\name=TwoWayTestItinerary;  
  
   version=;  
  
- **LDAP**  
  
   LDAP:\\\TransportType=SMTP;  
  
   TransportLocation={mail}  
  
   Filter=(&(objectClass=User)(|(userPrincipalName=yourname@domain.com)));  
  
   SearchRoot=;  
  
   SearchScope=Subtree;  
  
   EndpointConfig=Subject=Itinerary Test Message to {mail}& 
  
   SMTPAuthenticate=0&
  
   SMTPHost=127.0.0.1&
  
   From=test@globalbank.com&
  
   DeliveryReceipt=false&
  
   MessagePartsAttachments=0&
  
   ReadReceipt=false;  
  
   ThrowErrorIfNotFound=false;  
  
   Action=;  
  
   JaxRpcResponse=false;  
  
   MessageExchangePattern=;  
  
   TargetNamespace=;  
  
   TransformType=;  
  
  Not all attributes in the connection string are mandatory. In addition, **EndPointConfig** is a special attribute that any resolver can populate and return. Optionally, the resolver can store the name/value pairs that correspond to specific BizTalk Adapter Context properties, which it can, in turn, write to the context of the BizTalk message.  
  
  In this case, the **ResolverDictionary** instance that contains all the resolved properties returned from the resolution process then passes to the adapter manager. The adapter manager passes the dictionary to the specific adapter provider that will set all the adapter-specific and endpoint-specific BizTalk Context properties for the message. The resolvers look for the **EndPointConfig** property, extract the name/value pairs that correspond to their respective adapter properties, and then set these values on the message.  
  
## Supported Adapter Providers  
 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes the following built-in adapter providers: **FILE, FTP, SMTP,MQSeries, WCF-BasicHttp, WCF-WSHttp,** and **WCF-Custom**. The name of each adapter provider is identical to the name of the associated adapter (transport type) in BizTalk Server.  
  
 A major advantage of the Resolver and Adapter Provider Framework is that you can extend it by creating and registering your own custom resolvers to resolve endpoint information and custom adapter providers to set specific properties of registered BizTalk adapters. For more information, see [Modifying and Extending the BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).
