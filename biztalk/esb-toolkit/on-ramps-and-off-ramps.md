---
description: "Learn more about: On-Ramps and Off-Ramps"
title: "On-Ramps and Off-Ramps | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0cce5d2-f16f-4bda-94ac-20c4f457cfc7
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# On-Ramps and Off-Ramps
In an environment where [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is deployed, a BizTalk receive location responsible for receiving ESB-destined messages is referred to as an "on-ramp." To configure a standard BizTalk receive location to an ESB on-ramp, associate the receive location with one of the pipelines provided as part of the toolkit, and then correctly configure the components of that pipeline to determine or read the itinerary for the inbound message, depending on your scenario.  
  
 An ESB "off-ramp" corresponds to a BizTalk dynamic send port. As an itinerary is being processed, values are promoted to the context properties of the associated message using the System-Properties.xsd schema. The BizTalk publish-subscribe mechanism uses these promoted properties to route a message through a dynamic send port (off-ramp) to complete a message delivery.  
  
 The following table lists the on-ramps that are provided by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
|Name|Message exchange pattern|**Description**|  
|----------|------------------------------|---------------------|  
|ESB.ItineraryServices|One-Way|ASMX on-ramp; expects ESB itinerary content in SOAP header.|  
|ESB.ItineraryServices.Response|Request-Response|ASMX on-ramp; expects ESB itinerary content in SOAP header.|  
|ESB.ItineraryServices.WCF|One-Way|Windows Communication Foundation (WCF) on-ramp; expects ESB itinerary reference in SOAP header.|  
|ESB.ItineraryServices.Response.WCF|Request-Response|WCF on-ramp; expects ESB itinerary reference in SOAP header.|  
|ESB.ItineraryServices.Generic.WCF|One-Way|WCF on-ramp; expects request message only.|  
|ESB.ItineraryServices.Generic.Response.WCF|Request-Response|WCF on-ramp; expects request message only.|  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] on-ramps that are not ASMX should be configured to select ESB itineraries. For more information about how to select an ESB itinerary, see [Using a Pipeline Component to Select an Existing Itinerary](../esb-toolkit/using-a-pipeline-component-to-select-an-existing-itinerary.md).
