---
description: "Learn more about: Using the Resolver Components in Your Code"
title: "Using the Resolver Components in Your Code | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d197cb28-78a9-4c8a-872b-f61ef15e6622
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the Resolver Components in Your Code
The following code fragment from the dynamic transformation agent shows the default just-in-time (JIT) resolution functionality. You can easily implement resolution in your own application by using similar code.  
  
```  
  
//XLANGs  
itinerary = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryWrapper();  
step = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryStepWrapper();  
  
itinerary.Itinerary = Microsoft.Practices.ESB.Itinerary.ItineraryOMFactory.Create(InboundMessage);  
step.ItineraryStep = itinerary.Itinerary.GetItineraryStep(InboundMessage);  
resolvers = step.ItineraryStep.ResolverCollection;  
resolvers.MoveNext();  
resolver = resolvers.Current;  
  
// Pass the resolver configuration to the Resolver mgr for resolution.  
resolverDictionary = Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage, resolver);  
  
// Set the transform type.  
transformType = resolverDictionary.Item("Resolver.TransformType");  
```  
  
 In the preceding listing, the **Resolve** method of the **ResolverMgr** class returns a **Dictionary** object that contains all the default resolution properties and their resolved values. Any custom resolver can add custom properties to the **Dictionary** object; doing this makes those properties available to any custom itinerary service.  
  
 The following table shows the properties that can be optionally populated by the resolvers included in the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. Any itinerary service can retrieve these property values by extracting them from the returned **Dictionary** object.  
  
 **Properties**:  
  
|&nbsp;|&nbsp;|&nbsp;|  
|-|-|-|  
|**Resolver.Action**|**Resolver.ActionField**|**Resolver.DocumentSpecName**|  
|**Resolver.Success**|**Resolver.EndpointConfig**|**Resolver.DocumentSpecStrongName**|  
|**Resolver.FixJaxRpc**|**Resolver.InboundTransportType**|**Resolver.EpmRRCorrelationToken**|  
|**Resolver.InterchangeId**|**Resolver.IsRequestResponse**|**Resolver.InboundTransportLocation**|  
|**Resolver.MessageType**|**Resolver.MethodName**|**Resolver.MessageExchangePattern**|  
|**Resolver.ReceivePortName**|**Resolver.TransportLocation**|**Resolver.OutboundTransportCLSID**|  
|**Resolver.TransformType**|**Resolver.TargetNamespace**|**Resolver.ReceiveLocationName**|  
|**Resolver.TransportType**|**Resolver.TransportNamespace**|**Resolver.WindowUserField**|  
|**Resolver.CacheTimeout**|||  
  
 After the resolver manager returns the **Dictionary** object instance, the adapter manager sets the specific BizTalk Adapter Context properties of the message. The following code fragment from the routing agent demonstrates how you can use the adapter manager to set the endpoint properties of the outgoing message.  
  
```  
  
//XLANGs  
// Set the transport properties.  
transportLocation = resolverDictionary.Item("Resolver.TransportLocation");  
transportType = resolverDictionary.Item("Resolver.TransportType");  
  
// Create the delivery message.  
DeliveryMessage = InboundMessage;  
  
// Call the adapter manager to set all necessary properties on the message.  
Microsoft.Practices.ESB.Adapter.AdapterMgr.SetEndpoint(  
                                resolverDictionary,DeliveryMessage);  
  
// Set the delivery port address.  
DeliveryPort(Microsoft.XLANGs.BaseTypes.Address) = transportLocation;  
DeliveryPort(Microsoft.XLANGs.BaseTypes.TransportType) = transportType;  
```  
  
 The following code fragment from the routing agent demonstrates how to use the adapter manager from within a custom pipeline component to set the endpoint properties of an outgoing message.  
  
```csharp  
// Resolve the configuration for routing.  
ResolverDictionary = ResolverMgr.Resolve(info, pInMsg, pContext);  
  
// Call the adapter manager to set all required message properties.  
AdapterMgr.SetEndpoint(ResolverDictionary, pInMsg.Context);  
```
