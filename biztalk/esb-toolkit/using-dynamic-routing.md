---
description: "Learn more about: Using Dynamic Routing"
title: "Using Dynamic Routing"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Using Dynamic Routing
The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports dynamic routing of messages using a built-in process and a generic delivery agent; it also supports dynamic routing of messages at the messaging layer using the ESB Dispatcher or ESB Dispatcher Disassemble pipeline components.  
  
## Overview  
 The dynamic resolution mechanism in [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] enables discovery of endpoints when a message arrives or immediately before a message is delivered.  
  
## How It Works  
 The generic delivery agent provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is both a sample and a guide to the development and usage of dynamic routing techniques. You can easily create additional delivery agents or implement delivery agents consisting of just a send port (which do not implement an orchestration). By default, the ESB Dispatch and ESB Dispatch Disassembler pipeline components offer a much more optimized dynamic routing capability.  
  
 The generic delivery agent itself implements an orchestration that subscribes to messages where the **Name** attribute of the current **ServiceInstance** element in the itinerary is **Microsoft.Practices.ESB.Services.Routing**. The agent performs the following sequence of operations:  
  
1.  It receives an un-typed message (System.Xml.XmlDocument).  
  
2.  It attempts to resolve n number of endpoints using the resolver manager.  
  
3.  It uses the adapter manager to set the endpoint properties of the message context and the logical dynamic port.  
  
4.  It publishes the message through the direct-bound send port, which triggers the BizTalk Server subscription on the dynamic send port for further message routing.  
  
## How to Configure Dynamic Routing  
 For more information about how to configure dynamic routing using the Itinerary Designer, see Creating Itineraries Using Itinerary Designer.  
  
## Dynamic Routing Errors  
 The dynamic routing mechanism will create and publish an [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Fault message in the following cases:  
  
-   The delivery agent cannot determine the endpoint during just-in-time (JIT) resolution.  
  
-   A delivery failure occurs.  
  
-   No subscriber exists for the output message.  
  
-   Any system exception occurs.
