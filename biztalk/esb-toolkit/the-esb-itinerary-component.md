---
title: "The ESB Itinerary Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 379edc6a-7d53-4338-87a5-47b5238453a4
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The ESB Itinerary Component
The ESB Itinerary component sets the context properties from the SOAP header sent along with the message to an ESB itinerary on-ramp.  
  
## Installation  
 Installing the ESB Core automatically installs the **Itinerary** pipeline component in the BizTalk Server Pipeline Components folder.  
  
## How It Works  
 The ESB Itinerary component is a Microsoft BizTalk pipeline component that can reside only in a receive pipeline. It promotes values from either SOAP message headers or component settings into the message context as properties. You can find an example of promoting SOAP headers in the Itinerary On-Ramp Web services provided with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. These Web services expose SOAP headers as part of their contracts, and client applications must set the headers. As the message passes through the component in a receive pipeline, the component reads the SOAP header values and promotes (writes) them to the message context properties.  
  
## Using the ESB Itinerary Component  
 You can add the ESB Itinerary component to a receive pipeline and then use the pipeline in a receive location. The component automatically promotes SOAP header values or component settings into the context properties of the incoming message.  
  
 For an example of how to use this component, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).