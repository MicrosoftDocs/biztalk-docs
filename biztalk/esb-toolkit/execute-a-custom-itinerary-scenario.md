---
title: "Execute a Custom Itinerary Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6fd69e29-e853-4b16-9966-29ab98dd5bea
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Execute a Custom Itinerary Scenario
You can use the Itinerary Test Client application execute custom itinerary scenarios.  

### To execute a custom itinerary scenario using the Itinerary Test Client application  

1. In Windows Explorer, open the folder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test\bin\Debug where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples and start the application named Esb.Itinerary.Test.exe.  

2. Select a service type in the **ServiceType** drop-down list, specify a name for the request, and then select the **IsRequestResponse** check box if this is a request/response operation. You can specify a two-way operation and choose to use the WCF version of the Itinerary Web service; to do this, select the check boxes in the **Web Service Options** section at the top of the application window.  

3. To specify the resolvers to use with the selected service in the **AddResolversfortheService** section of the window, select a resolver type from the drop-down list, and then click **AddResolver**. You can add more than one resolver if required. After you add all the required resolvers, click the **AddService** button to add this service invocation to the itinerary.  

4. If you want to add more service invocations to the itinerary, repeat steps 2 and 3. You can also use the **RemoveService** and **ClearServices** buttons to modify the list of services in the itinerary.  

5. If you want to repeat the current itinerary at another time, save the complete current itinerary to disk by clicking the **SaveItinerary** button. You can load it again by clicking the **LoadItinerary** button. This means that you do not have to specify the services and resolvers in the itinerary every time you execute this scenario with different messages or Itinerary Web service settings.  

6. Load a suitable message. To do this, either type the path and name of the message in the **LoadMessage** text box or click the ellipsis button (...), and then select the required message file.  

7. Click the **SubmitRequest** button to submit the message for processing with the itinerary settings you specified. If the processing returns a result, this will appear in the **Result** text box.
