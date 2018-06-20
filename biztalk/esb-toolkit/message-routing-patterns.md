---
title: "Message Routing Patterns | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d95c5ba0-122f-4793-bfce-a95830dfe094
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Routing Patterns
Message routing patterns define proven guidelines for routing a message to its target endpoint(s). Routing can be the result of static configuration, or it can be dynamically configured based on a number of criteria and using a number of methods.  
  
## Message Router  
 The Message Router pattern determines the recipient of the message based on a set of conditions. For a detailed description of this pattern, see [Message Router](http://go.microsoft.com/fwlink/?LinkId=186844) ([http://go.microsoft.com/fwlink/?LinkId=186844](http://go.microsoft.com/fwlink/?LinkId=186844)) on the Enterprise Integration Patterns site.  
  
 The implementation of this pattern in the Itinerary Designer is a combination of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary routing service and a single content-based resolver. The itinerary routing service is responsible for promoting message routing properties in Microsoft BizTalk message context or for explicit routing of a message.  
  
 You can choose the itinerary routing service provided by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] as follows:  
  
- Define the itinerary routing service with a messaging extender to execute in a BizTalk pipeline using Itinerary Designer.  
  
- Define the itinerary routing service with an orchestration extender to execute as an orchestration using Itinerary Designer that performs routing using BizTalk send ports.  
  
  The resolver associated with the itinerary routing service determines the recipient of the message, based on the message content. You can choose from the resolvers that support content-based routing provided by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], or you can implement your own resolver.  
  
  For an example of implementing this pattern in the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], see the following resources:  
  
- [How to: Resolve a Service Endpoint Using a UDDI Binding Key Search](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  
  
- [How to: Resolve a Service Endpoint Using a UDDI Category Search](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  
  
## Content-Based Router  
 The Content-Based Router pattern determines the recipient of a message based on message content. For a detailed description of this pattern, see [Content-Based Router](http://go.microsoft.com/fwlink/?LinkId=186839) ([http://go.microsoft.com/fwlink/?LinkId=186839](http://go.microsoft.com/fwlink/?LinkId=186839)) on the Enterprise Integration Patterns site.  
  
 The implementation of this pattern in Itinerary Designer is a combination of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary routing service and a single content-based resolver. The itinerary routing service is responsible for promoting message routing properties in the BizTalk message context or for explicitly routing a message.  
  
 You can choose the itinerary routing service provided by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] as follows:  
  
- Define an itinerary routing service with a messaging extender to execute in a BizTalk pipeline using Itinerary Designer.  
  
- Define an itinerary routing service with an orchestration extender to execute as an orchestration using Itinerary Designer, which performs routing using BizTalk send ports.  
  
- Define an itinerary broker service with a broker messaging extender to execute in a BizTalk pipeline using Itinerary Designer.  
  
  The resolver associated with itinerary routing service determines the recipient of the message based on the message content. You can choose from the following resolvers that support content-based routing provided by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:  
  
- **XPATH resolver**. By using this resolver, you can route message content using XPATH queries.  
  
- **BRE resolver**. By using this resolver, you can retrieve routing information from message content using the BizTalk Rules Engine.  
  
- **Message Context resolver**. By using this resolver, you can retrieve the content of a message from the BizTalk message context when it is associated with a [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary broker service.  
  
  > [!NOTE]
  >  In addition to the preceding implementation scenarios, you can develop a custom content-based resolver and itinerary routing solution as a messaging-based or orchestration-based service. In this case, you may need to implement extenders for the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] resolver and itinerary service to interoperate with the Itinerary Designer.  
  
  For example of this implementation, see the following resources:  
  
- [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)  
  
- [How to: Implement Content-Based Routing Using a Business Rules Policy for a Known Message Type](../esb-toolkit/apply-content-based-routing-using-business-rules-policy-for-known-message-type.md)  
  
- [How to: Dynamically Route a Message Based on Message Context Using a Business Rules Policy](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
## Routing Slip  
 The Routing Slip pattern describes a scenario in which a message must be routed through a series of components in a pre-defined order, which may not be known at the design time. For a detailed description of this pattern, see [Routing Slip](http://go.microsoft.com/fwlink/?LinkId=186840) ([http://go.microsoft.com/fwlink/?LinkId=186840](http://go.microsoft.com/fwlink/?LinkId=186840)) on the Enterprise Integration Patterns site.  
  
 The implementation of this pattern is provided by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]; its implementation depends on the type of client application that submits a message for itinerary-based processing:  
  
- **Service proxy**. With this type of application, configure the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] on-ramp with the Itinerary Selector pipeline component and associate an itinerary resolver to select the appropriate [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary. The itinerary properties may be configured as static properties using ITINERARY resolver, or they can be configured as dynamic properties using BizTalk Rules Engine and BRI resolver.  
  
- **Advanced client**. With this type of application, configure the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] on-ramp with the Itinerary Selector pipeline component and the ITINERARY-STATIC resolver. The client application sends a message with an itinerary reference header, which contains the itinerary name, version, and tracking identifier.  
  
- **Adaptive client**. With this type of application, the client application invokes the resolver service, which, in turn, identifies the itinerary reference by passing the client state as a request message. If the itinerary is resolved, the client application submits a message with itinerary references in the same way as in the preceding advanced client scenario.  
  
  For more information about implementing this pattern, see the following resources:  
  
- [How to: Select an Itinerary Using a Business Rules Policy](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
- [How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
  > [!NOTE]
  >  In addition to the preceding scenarios, you can develop a custom itinerary resolver and itinerary routing services. You may consider creating designer extenders for custom itinerary services for use in the Itinerary Designer.  
  
## Scatter-Gather  
 The Scatter-Gather pattern enables messages to be sent to multiple recipients and to aggregate their responses; this results in a single message. For a detailed description of this pattern, see [Scatter-Gather](http://go.microsoft.com/fwlink/?LinkId=186841) ([http://go.microsoft.com/fwlink/?LinkId=186841](http://go.microsoft.com/fwlink/?LinkId=186841)) on the Enterprise Integration Patterns site.  
  
 For an example of implementing this pattern, see the [Installing and Running the Scatter-Gather Sample](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md) sample.  
  
## Recipient List  
 The Recipient List pattern addresses the scenario solution in which a message is routed to one or more recipients. The recipient list can be defined either statically (meaning it has a fixed list of recipients) or dynamically. For a detailed description of this pattern, see [Recipient List](http://go.microsoft.com/fwlink/?LinkId=186842) ([http://go.microsoft.com/fwlink/?LinkId=186842](http://go.microsoft.com/fwlink/?LinkId=186842)) on the Enterprise Integration Patterns site.  
  
 The implementation of this pattern in Itinerary Designer is a combination of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary routing service and multiple resolvers. The itinerary routing service is responsible for cloning a message and then using its BizTalk message context properties to explicitly route a message.  
  
 You can choose the itinerary routing service provided by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] as follows:  
  
- Define the itinerary routing service with a messaging extender to execute in the BizTalk pipeline using Itinerary Designer.  
  
- Define the itinerary routing service with a messaging extender to execute as an orchestration using Itinerary Designer, which performs routing using BizTalk send ports.  
  
  The resolver associated with itinerary routing service determines the recipient of the message based on the message content. You can choose the set of resolvers provided by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] to implement this scenario. For more information about implementing this pattern, see the following resource:  
  
- [How to: Route a Single Message to Multiple Recipients Using an Itinerary Routing Slip](../esb-toolkit/route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip.md)  
  
## Splitter  
 The Splitter pattern addresses the problem when a single message needs to be split into multiple messages. For a detailed description of this pattern, see [Splitter](http://go.microsoft.com/fwlink/?LinkId=186843) ([http://go.microsoft.com/fwlink/?LinkId=186843](http://go.microsoft.com/fwlink/?LinkId=186843)) on the Enterprise Integration Patterns site. For more information about implementing this pattern, see the following resource:  
  
-   [How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)