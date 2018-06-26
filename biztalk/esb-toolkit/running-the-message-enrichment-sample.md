---
title: "Running the Message Enrichment Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7015a2fe-3727-48f3-a2ed-c368e0630626
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running the Message Enrichment Sample
The Message Enrichment sample uses a Windows Forms test client application provided with the Itinerary On-Ramp sample.  
  
 **To run Message Enrichment sample**  
  
1. If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.  
  
2. In Windows Explorer, open the folder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then start the application named Esb.Itinerary.Test.exe.  
  
3. Clear the **Use WCF Service** check box so that a client-side itinerary can be utilized.  
  
4. Click the **Load Itinerary** button, and then select one of the sample itineraries located in the \Source\Samples\MessageEnrichment\Itineraries folder.  
  
5. Click the **LoadMessage** button, and then select the OrderDoc.xml sample message from the \Source\Samples\MessageEnrichment\Test\ folder.  
  
6. Click the **SubmitRequest** button to send the request to the Itinerary On-Ramp service.  
  
7. Browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out\\%MessageID%.xml to see the output message.  
  
   For information about how the Message Enrichment sample works, see [How the Message Enrichment Sample Works](../esb-toolkit/how-the-message-enrichment-sample-works.md).