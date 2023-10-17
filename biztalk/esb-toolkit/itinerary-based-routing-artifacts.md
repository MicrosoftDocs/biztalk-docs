---
description: "Learn more about: Itinerary-Based Routing Artifacts"
title: "Itinerary-Based Routing Artifacts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cff38ab7-5a16-42cc-9065-075e9db7acd3
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Itinerary-Based Routing Artifacts
The itinerary-based routing capabilities of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] include a set of key artifacts defined in multiple assemblies. The following tables list these artifacts by category to assist developers when working with and extending the itinerary-based routing implementation with additional ESB itinerary service implementations.  
  
## ESB Itinerary Classes  
 The following table lists the assemblies and artifacts contained in the ESB.Itinerary project. The name of the containing assembly is **Microsoft.Practices.ESB.Itinerary.dll**.  
  
|Key artifact|Description|  
|------------------|-----------------|  
|**MessageHelper**|Contains all the private functions called by other project artifacts.|  
|**IItineraryStep**|The public class returned from the **GetItineraryStep** method.|  
|**ResolverCollection**|Implements a collection of all the resolvers associated with a service. This class is exposed by the **IItineraryStep** interface and is populated by the **GetItineraryStep** method.|  
|**IMessagingService**|Defines the interface implemented by messaging-based itinerary services.|  
|**IMessagingService**|Factory for creating **IMessagingService** objects based on a name configured in Esb.config.|  
  
## ESB Itinerary Messaging Services  
 The following table lists the classes defined in the **Microsoft.Practices.ESB.Itinerary.Services.dll** assembly in **Microsoft.Practices.ESB.Itinerary.Services** namespace.  
  
|Key artifact|Description|  
|------------------|-----------------|  
|**Routing**|Implementation of the ESB itinerary messaging routing: invoked by ESB Dispatcher or Dispatcher Disassemble components using the Esb.config file.|  
|**Transform**|Implementation of the ESB itinerary messaging transformation service: invoked by ESB Dispatcher or Dispatcher Disassemble components using the Esb.config file.|  
  
 The following table lists the artifacts contained in the **Microsoft.Practices.ESB.Itinerary.Services.Broker.dll** assembly.  
  
|Key artifact|Description|  
|------------------|-----------------|  
|**MessagingBroker**|Implementation of the ESB itinerary messaging service for routing by message context: invoked by ESB Dispatcher or Dispatcher Disassemble components using the Esb.config file.|  
  
 These services are also defined in the BizTalk ESB Toolkit configuration file, Esb.config.  
  
## ESB Itinerary Orchestration Services  
 The following table lists the artifacts contained in the **Microsoft.Practices.ESB.Agents.dll** assembly.  
  
|Key artifact|Description|  
|------------------|-----------------|  
|Delivery.odx|A sample routing orchestration itinerary service identified by the service name **Microsoft.Practices.ESB.Services.Routing**.|  
|Transform.odx|A sample transformation orchestration itinerary service identified by the service name **Microsoft.Practices.ESB.Services.Transform**.|  
  
## ESB Itinerary Pipeline Components  
 The following table lists the assemblies and artifacts contained in the **Microsoft.Practices.ESB.Itinerary.PipelineComponents.dll** assembly.  
  
|Key artifact|Description|  
|------------------|-----------------|  
|**Itinerary**|The primary itinerary processing pipeline component that processes and validates the itinerary of incoming messages.|  
|**ItineraryCache**|The itinerary caching pipeline component for use in Solicit-Response send ports.|  
|**ItinerarySelector**|The itinerary selector pipeline component that resolves server-side itineraries in generic on-ramps.|  
  
## ESB Itinerary Pipelines  
 The following table lists the assemblies and artifacts contained in the **Microsoft.Practices.ESB.Itinerary.Pipelines.dll** assembly.  
  
|Key artifact|Description|  
|------------------|-----------------|  
|ItineraryReceive|The itinerary pipeline used in the Itinerary Web service on-ramp. Used as a receive pipeline for receive locations and contains the following pipeline components:<br /><br /> ESB Itinerary, XML Disassembler, ESB Dispatcher|  
|ItineraryReceivePassthrough||  
|ItineraryReceiveXml|The itinerary pipeline used in the Itinerary Web service on-ramp. Used as a receive pipeline for receive locations to route an incoming message to multiple endpoints and contains the following pipeline components:<br /><br /> ESB Itinerary, ESB Dispatcher Disassembler|  
|ItinerarySend|The itinerary pipeline used in the Itinerary off-ramp. Used as a send pipeline for a send port and contains the following pipeline components:<br /><br /> ESB Dispatcher, XML Assembler, ESB Itinerary Cache|  
|ItinerarySendPassthrough|The itinerary pipeline used in the Itinerary off-ramp. Used as a send pipeline for a send port and contains the following pipeline components:<br /><br /> ESB Dispatcher, ESB Itinerary Cache|  
|ItinerarySendReceive|The itinerary pipeline used in the Itinerary off-ramp. Used as a receive pipeline for a Solicit-Response send port and contains the following pipeline components:<br /><br /> ESB Itinerary Cache, XML Disassembler, ESB Dispatcher|  
|ItineraryForwarderSendReceive|The itinerary pipeline used in the Itinerary off-ramp. Used as a receive pipeline for a send port and contains the following pipeline components:<br /><br /> ESB Itinerary Cache, XML Disassembler, ESB Dispatcher, Forwarder|  
|ItineraryForwarderSendReceiveXml|The itinerary pipeline used in the Itinerary Web service on-ramp. Used as a receive pipeline for a send port and contains the following pipeline components:<br /><br /> ESB Itinerary Cache, ESB Dispatcher Disassemble, Forwarder|  
|ItinerarySelectReceive|The itinerary pipeline used in the Itinerary Web service on-ramp. Used as a receive pipeline for receive locations and contains the following pipeline components:<br /><br /> ESB Itinerary Selector, XML Disassembler, ESB Dispatcher|  
|ItinerarySelectReceivePassthrough|The itinerary pipeline used in the Itinerary Web service on-ramp. Used as a receive pipeline for receive locations and contains the following pipeline components:<br /><br /> ESB Itinerary Selector, ESB Dispatcher|  
|ItinerarySelectReceiveXml|The itinerary pipeline used in the Itinerary Web service on-ramp. Used as a receive pipeline for receive locations and contains the following pipeline components:<br /><br /> XML Disassembler, ESB Itinerary Selector, ESB Dispatcher|  
|ItinerarySelectSendReceive|The itinerary pipeline used in the Itinerary off-ramp. Used as a receive pipeline for a send port and contains the following pipeline components:<br /><br /> ESB Itinerary Cache, ESB Itinerary Selector, XML Disassembler, ESB Dispatcher|  
  
## ESB Itinerary Schemas  
 The following table lists the assemblies and artifacts contained in the **Microsoft.Practices.ESB.Itinerary.Schemas.dll** assembly.  
  
|Key artifact|Description|  
|------------------|-----------------|  
|Itinerary.xsd|Defines the ESB itinerary SOAP headers used in Windows Communication Foundation (WCF)–based and SOAP–based Web service on-ramps.|  
|ItineraryDescription.xsd|This scehma represents itinerary reference data and should be used for submitting message to WCF–based on-ramps.|  
|System-Properties.xsd|Defines the ESB itinerary–related BizTalk Context properties.|
