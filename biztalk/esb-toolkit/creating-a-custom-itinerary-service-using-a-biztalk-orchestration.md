---
title: "Creating a Custom Itinerary Service Using a BizTalk Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bd7ed38-02a3-41b1-9990-754d5539f15e
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating a Custom Itinerary Service Using a BizTalk Orchestration
The itinerary framework that is part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports execution of itinerary steps using orchestrations. You can implement a custom itinerary service as a Microsoft BizTalk Server orchestration based on your functional requirements, which may include the following:  
  
- Multiple service invocations (as demonstrated by the [Installing and Running the Scatter-Gather Sample](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md))  
  
- Protocol mediation and message correlation (for example, HTTP-MQSeries)  
  
- Complex routing decisions based on message enrichment from external data sources  
  
- Business processing logic  
  
  Every itinerary service implemented using a BizTalk Server orchestration is responsible for the following:  
  
- Exception and error handling using the ESB Exception Handling Framework or optional custom exception handlers that support resubmission (one-way itineraries)  
  
- Advancing the itinerary and publishing outbound messages through BizTalk Server so that the next itinerary service step can execute  
  
#### To create a custom itinerary service using a BizTalk Server orchestration  
  
1. Create new BizTalk Server project containing a new orchestration; for example, MyCustomeItineraryService.odx.  
  
2. Add references to the following assemblies:  
  
   -   **Microsoft.Practices.ESB.Itinerary**  
  
   -   **Microsoft.Practices.ESB.Itinerary.Schemas**  
  
   -   **Microsoft.Practices.ESB.ExceptionHandling**  
  
   -   **Microsoft.Practices.ESB.ExceptionHandling.Faults**  
  
3. Define a logical direct-bound receive port and an activated receive shape in the orchestration.  
  
4. Define a subscription filter to activate the orchestration from the message itinerary context so that the orchestration executes the **MyCustomItineraryService** step. The following code shows an example of a suitable filter.  
  
   ```csharp  
   (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName   
       == "MyCustomItineraryService")   
   && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState == "Pending")  
   && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType   
       == "Orchestration")  
   ```  
  
5. Define an orchestration of type **Microsoft.Practices.ESB.Itinerary.ItineraryStep**. Add an expression activity to the orchestration that populates this variable, as shown in the following code.  
  
   ```csharp  
   // Retrieve the current itinerary step.  
   itinerary = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryWrapper();  
   step = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryStepWrapper();  
  
   itinerary.Itinerary = Microsoft.Practices.ESB.Itinerary.ItineraryOMFactory.Create(InboundMessage);  
   step.ItineraryStep = itinerary.Itinerary.GetItineraryStep(InboundMessage);  
  
   ```  
  
6. Add your custom implementation to the itinerary that creates the outbound message for the next itinerary steps; for example, OutboundMsg.  
  
7. Advance the itinerary using the following expression activity that uses the message context from inbound message.  
  
   ```csharp  
   OutboundMessage(*) = InboundMessage(*);   
   itinerary.Itinerary.Advance(OutboundMessage, itineraryStep.ItineraryStep);  
   ```  
  
8. Send the outbound message with the updated itinerary through a direct-bound send port to activate the next itinerary service.  
  
   For more information about implementing a custom itinerary service using BizTalk Server orchestrations, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md) and [Installing and Running the Scatter-Gather Sample](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md).