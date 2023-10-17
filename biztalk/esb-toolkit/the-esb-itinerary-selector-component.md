---
description: "Learn more about: The ESB Itinerary Selector Component"
title: "The ESB Itinerary Selector Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2cd8a85-e036-4817-9541-3fd720ca04ef
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The ESB Itinerary Selector Component
The ESB Itinerary Selector component allows incoming messages that do not have the itinerary SOAP header to pass through the ESB by selecting an appropriate server-side itinerary for the message with the help of a resolver. The component is also used for messages that use a SOAP header to define the name and version of an itinerary, as requested by the client.  
  
## Installation  
 Installing the ESB Core automatically installs the **ItinerarySelector** component in the BizTalk Server Pipeline Components folder.  
  
## How It Works  
 The ESB Itinerary Selector component is a Microsoft BizTalk pipeline component that can reside only in a receive pipeline. The component selects a server-side itinerary for use in processing a message. As the message passes through the component in a receive pipeline, the component reads its configuration and uses the **ResolverConnectionString** property to call the correct resolver to look up the appropriate itinerary to use when processing the message. The Itinerary Selector component then performs the same steps as the Itinerary pipeline component to validate the message and promote the properties necessary to ensure the message continues to the next processing stage.  
  
## Using the ESB Itinerary Selector Component  
 You can add the ESB Itinerary component to a receive pipeline and then use the pipeline in a receive location. When this component is configured with the ITINERARY-STATIC resolver in WCF on-ramp, the name and version of the itinerary requested by the client (as represented in the SOAP header) will be retrieved from the message context and used to select the appropriate itinerary.  
  
## Component Properties  
 The ESB Itinerary Selector component exposes three public properties:  
  
-   **IgnoreErrorKey**. This property defines whether, if an error is returned by the resolver, the message should be processed without the itinerary (when set to **True**) or suspended.  
  
-   **ItineraryFactKey**. This represents the key in the dictionary returned by the resolver that contains the actual XML of the Itinerary selected. Generally, **Resolver.Itinerary**, unless a custom resolver is used.  
  
-   **ResolverConnectionString**. This is a resolver connection string that contains name-value pairs that a resolver can use to select and/or look-up an itinerary.
