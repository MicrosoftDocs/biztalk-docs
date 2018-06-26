---
title: "Running the Multiple Web Services Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b201c7c3-213a-4009-8872-5a4c1cbb8195
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running the Multiple Web Services Sample
The Multiple Web Services sample uses the Windows Forms test client application provided with the Itinerary On-Ramp sample.  
  
 **To run the Multiple Web Services sample**  
  
1. If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.  
  
2. In Windows Explorer, open the folder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then start the application named Esb.Itinerary.Test.exe.  
  
3. Clear the **Use WCF Service** check box, so that a client-side itinerary can be utilized.  
  
4. Click the **Load Itinerary** button, and then select one of the sample itineraries located in the \Source\Samples\MultipleWebServices\Itineraries folder.  
  
5. Select the **Two Way Service** check box so the application will perform a two-way itinerary services operation.  
  
6. Click the **LoadMessage** button, and then select the NAOrderDoc.xml sample message from the \Source\Samples\Itinerary\Test\Data folder.  
  
7. Click the **SubmitRequest** button to send the request to the Itinerary On-Ramp service. Wait for a response message to appear in the **Result** box.  
  
   For information about how the Multiple Web Services sample uses the ESB Itinerary service, see [How the Multiple Web Services Sample Works](../esb-toolkit/how-the-multiple-web-services-sample-works.md).