---
description: "Learn more about: The ESB Itinerary Forwarder Component"
title: "The ESB Itinerary Forwarder Component"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The ESB Itinerary Forwarder Component
The ESB Itinerary Forwarder component is used when an itinerary must sequentially invoke multiple Web services. The component can be used in receive pipelines that are associated with the response side of a two-way off-ramp.  
  
## Installation  
 Installing the ESB Core automatically installs the **Itinerary Forwarder** component in the BizTalk Server Pipeline Components folder.  
  
## How It Works  
 When Microsoft BizTalk receives a message through a two-way receive port as the message is published to the Message Box database, an instance subscription is created. This subscription consists of the **EpmRRCorrelationToken** promoted property and a **RouteDirectToTP** promoted property. When the subscriber (orchestration or two-way send port) returns the response message, these promoted properties match the subscription and the response is immediately returned through the send pipeline of the receive port.  
  
 The ESB Itinerary Forwarder should be used in the response pipeline for a two-way off-ramp where the off-ramp is calling a request-response Web service. The component interferes with the typical BizTalk process by changing the **RouteDirectToTP** promoted property to False, thus ensuring that the response will not be returned to the initiating receive port. After the last step in the itinerary is reached, the **RouteDirectToTP** property is changed back to **True**, thus returning the result to the initiating on-ramp.  
  
## Using the ESB Itinerary Forwarder Component  
 Add the ESB ItineraryForwarder component to a receive pipeline and then use the pipeline with the response portion of a two-way off-ramp. Create an itinerary that chains multiple Web services, with or without transformation itinerary services, before or between the services. For an example of how to use the ESB Itinerary Forwarder Component, see the [Installing and Running the Multiple Web Services Sample](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md).
