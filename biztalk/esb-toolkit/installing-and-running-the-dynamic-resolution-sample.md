---
title: "Installing and Running the Dynamic Resolution Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4359987-b18c-44f5-a2cf-e30e17ac5e9f
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installing and Running the Dynamic Resolution Sample
The Dynamic Resolution sample demonstrates typical usage scenarios for the ESB Dispatcher and ESB Dispatcher Disassembler pipeline components. It demonstrates how you can use the components to dynamically resolve endpoint location, set routing properties, and resolve and execute Microsoft BizTalk maps at the messaging level without using an orchestration. It also demonstrates both one-way and two-way messaging patterns.  
  
> [!NOTE]
>  For optimum results when familiarizing yourself with the resolution mechanism within the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], you should run the [Installing and Running the Resolver Service Sample](../esb-toolkit/installing-and-running-the-resolver-service-sample.md) before you run the Dynamic Resolution sample.  
  
 The sample application contains two receive locations and two dynamic send ports, which the sample uses to demonstrate multiple use cases for the dynamic resolution components. Each use case shows how the resolvers and adapter providers in the Resolution and Adapter Provider Framework, when used in combination, can provide the basis for a variety of loosely coupled messaging solutions.  
  
## One-Way Messaging Scenarios  
 All one-way messaging scenarios (except the one that uses the XPATH Resolver) use the file NAOrderDoc.xml, located in the \Source\Samples\DynamicResolution\Test\Data folder, as input to the receive location named DynamicResolution_FILE. There are seven one-way messaging examples, all represented by a unique binding file that you must import before you execute each example.  
  
## Two-Way Messaging Scenarios  
 All two-way messaging scenarios use the sample ESB.NorthAmericanServices Web service located at http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx to publish the request message into BizTalk. You can execute this Web service using Microsoft InfoPath or through a utility such as the Storm available from [CodePlex](http://go.microsoft.com/fwlink/?LinkID=187762&clcid=0x409).  
  
 Each example dynamically resolves the endpoint URL to submit the message to the sample ESB.CanadianServices Web service located at http://localhost/ESB.CanadianServices/SubmitPOService.asmx. The example will execute either the **submitOrder** action or the **submitPurchase** action, depending on the results of the resolution process. The receive location for two-way messaging scenarios is DynamicResolutionReqResp_SOAP. There are 10 two-way messaging examples, all represented by a unique binding file that you must import before you execute each example.  
  
## Binding Files  
 The binding files for this sample are located in the folder named \Source\Samples\DynamicResolution\Samples\Release.  
  
 The binding file names all start with GlobalBank.ESB.DynamicResolution_SubmitOrder_To, followed by an indication of the individual example to which they apply. For example, the binding file for the "File Inbound to File Outbound using the STATIC Resolver" example is GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_STATIC_Bindings.xml.  
  
 Every time you import one of the binding files into the GlobalBank.ESB BizTalk application, the underlying receive location within the sample application is reset. The associated dynamic send port filters on the receive port name. Therefore, to execute a test, you just import one of the binding files and either drop the appropriately named message into the input folder (for one-way messaging scenarios) or call the NorthAmerican Web service using InfoPath, the Storm utility, or any other suitable client.  
  
## Sample Dependencies  
 The Dynamic Resolution sample has dependencies on a number of assemblies that are part of the core ESB installation. These assemblies are the following:  
  
- **Microsoft.Practices.ESB.PipelineComponents.dll**. This contains the ESB Dispatcher Pipeline component.  
  
- **Microsoft.Practices.ESB.Resolver.dll**. This implements the Resolver Manager called by the pipeline.  
  
- **Microsoft.Practices.ESB.Resolver.BRE.dll**. This implements the Business Rules Engine Resolver.  
  
- **Microsoft.Practices.ESB.Resolver.STATIC.dll**. This implements the STATIC Resolver.  
  
- **Microsoft.Practices.ESB.Resolver.UDDI.dll**. This implements the UDDI Resolver.  
  
- **Microsoft.Practices.ESB.Resolver.UDDI3.dll**. This implements the UDDI3 Resolver.  
  
- **Microsoft.Practices.ESB.Resolver.XPATH.dll**. This implements the XPATH Resolver.  
  
- **Microsoft.Practices.ESB.Resolver.Schemas.dll**. This contains the resolver schemas.  
  
- **Microsoft.Practices.ESB.Adapter.dll**. This implements the adapter manager.  
  
- **Microsoft.Practices.ESB.Adapter.FTP.dll**. This implements the FTP adapter provider.  
  
- **Microsoft.Practices.ESB.Adapter.FILE.dll**. This implements the FILE adapter provider.  
  
- **Microsoft.Practices.ESB.Adapter.MQSeries.dll**. This implements the MQSeries adapter provider.  
  
- **Microsoft.Practices.ESB.Adapter.WcfBasicHttp.dll**. This implements the WCF-BasicHttp adapter provider.  
  
- **Microsoft.Practices.ESB.Adapter.WcfWSHttp.dll**. This implements the WCF-WSHttp adapter provider.  
  
  The Dynamic Resolution sample is also dependent on correct configuration of the preceding resolvers and adapters. Make sure that you complete the process for configuring these, as described in Installing the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
  This section contains the following topics:  
  
- [Installing the Dynamic Resolution Sample](../esb-toolkit/installing-the-dynamic-resolution-sample.md)  
  
- [Running the Dynamic Resolution Sample](../esb-toolkit/running-the-dynamic-resolution-sample.md)
