---
title: "Running the Designer Extensibility Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05ac3b50-5bf2-4566-8654-472391476d1f
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running the Designer Extensibility Sample
The Designer Extensibility sample uses two sample extenders to demonstrate how you can provide design-time configuration options for custom resolvers and for itinerary services.  
  
 **To run the Designer Extensibility sample**  
  
1.  Start Visual Studio.  
  
2.  In Visual Studio, point to **New** on the **File** menu, and then click **Project**.  
  
3.  Select the C# Class Library template, type **ItineraryLibrary** in the **Name** box, and then click **OK**.  
  
4.  In Solution Explorer, right-click the ItineraryLibrary project, point to **Add**, and then click **New Itinerary**.  
  
5.  In the **Name** box, type **TestItinerary**, and then press ENTER.  
  
6.  In the Toolbox, click an On-Ramp model element, and then drag it to the design surface.  
  
7.  In the Toolbox, click an Itinerary Service model element, and then drag it to the design surface.  
  
8.  In the Toolbox, click another Itinerary Service model element, and then drag it to the design surface.  
  
9. In the Toolbox, click an Off-Ramp model element, and then drag it to the design surface.  
  
10. In the Toolbox, click the Connector tool, and then drag a connection between the **OnRamp1** model element and the **ItineraryService1** model element.  
  
11. In the Toolbox, click the Connector tool, and then drag a connection between the **ItineraryService1** model element and the **ItineraryService2** model element.  
  
12. In the Toolbox, click the Connector tool, and then drag a connection between the **ItineraryService2** model element and the **OffRamp1** model element.  
  
13. Click the **OnRamp1** model element, and then in the Properties window, set the Extender property to **On-Ramp ESB Service Extension**.  
  
14. Set the **BizTalk Application** property to **Microsoft.Practices.ESB**.  
  
15. Set the **Receive Port** property to **OnRamp.Itinerary**.  
  
16. Click the **ItinearyService1** model element, and then in the Properties window, set the **Extender** property to **Sample Orchestration Itinerary Service Extension**.  
  
    > [!NOTE]
    >  This is the custom extension installed as part of the Designer Extensibility sample. It allows you to add properties to the property bag passed to an orchestration-based itinerary service.  
  
17. Set the **OtherValue** property to **1**.  
  
18. Set the **ServiceName** property to **Microsoft.Practices.ESB.Services.Routing**.  
  
19. Set the **SomeValue** property to **2**.  
  
20. Right-click the **Resolver** collection of **ItineraryService1**, and then click **Add new Resolver**.  
  
21. Click **Resolver1**, and then in the Properties window, set the **Resolver Implementation** property to **Sample Resolver Extension**.  
  
22. Set the **SomeResolverValue** property to **test**, and then set the version property to **1.0**.  
  
23. Click the **ItineraryService2** model element, and then in the Properties window, set the **Itinerary Service Extender** property to **Off-Ramp Itinerary Service Extension**.  
  
24. Set the **Off-Ramp** property to **OffRamp1 > Send Handlers**.  
  
25. Click the **OffRamp1** model element, and then in the Properties window, set the **Extender** property to **Off-Ramp ESB Service Extension**.  
  
26. Set the **BizTalk Application** property to **GlobalBank.ESB**.  
  
27. Set the **Send Port** property to **DynamicResolutionOneWay**.  
  
28. Right-click the design surface, and then click **Export Model**.  
  
29. Examine the generated XML.  
  
    > [!NOTE]
    >  Notice the **PropertyBag** element and the properties it contains. Also notice the Sample resolver connection string and how it was configured based on the properties entered.