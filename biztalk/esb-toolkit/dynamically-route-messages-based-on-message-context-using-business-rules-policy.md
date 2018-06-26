---
title: "How to: Dynamically Route a Message Based on Message Context Using a Business Rules Policy | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d3b68de-6b24-46fe-ae0d-91afb630bc19
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Dynamically Route a Message Based on Message Context Using a Business Rules Policy
## Goal  
 This section demonstrates how to create an itinerary that determines message endpoints, based on message context properties, using a BizTalk Server Business Rules Engine (BRE) policy, and then routes the message using the BizTalk Server FILE adapter.  
  
 In this How-to topic, you will complete the following steps:  
  
-   Create a business rules policy to evaluate message type.  
  
-   Create an itinerary routing slip to dynamically route using a business rules policy.  
  
-   Test the itinerary using the Itinerary Test Client sample application.  
  
## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## Steps  
 **To create a BRE policy to route a message using message context properties**  
  
1. Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **Business Rule Composer**.  
  
2. In Policy Explorer, right-click **Policies**, and then click **Add New Policy**. Name the policy **RouteBasedOnMessageType**.  
  
   **To add a routing rule for North American orders**  
  
3. In the **RouteBasedOnMessageType** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**. Name the rule **SetNAOrderEndpoint**.  
  
4. In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.  
  
5. In Facts Explorer, expand the **ESB.ContextInfo** vocabulary, expand **Version 1.0**, and then drag the **Context Message Type** fact to the **argument1** node under **Conditions**.  
  
   > [!NOTE]
   >  The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes several vocabularies that can be used for creating rules. Some of these should be replaced or augmented with your own vocabularies. For example, the **DynamicRunTimeMaptypes** policy has definitions for the maps provided in the **GlobalBank** samples.  
  
6. Click the **argument2** node, and then type **http://globalbank.esb.dynamicresolution.com/northamericanservices/#OrderDoc**  
  
7. In Facts Explorer, expand the **ESB.EndPointInfo** vocabulary, expand **Version 1.0**, and then drag the **Set End Point Outbound Transport Location** definition to **Actions**.  
  
8. Click **\<empty string\>**, and then type **C:\HowTos\Out\NorthAmerica%MessageID%.xml**  
  
9. From Facts Explorer, drag the **Set End Point Outbound Transport Type** definition to **Actions**.  
  
10. In Facts Explorer, expand the **ESB.TansportTypes** vocabulary, expand **Version 1.0**, and then drag the **Adaptor Providers** definition to **\<empty string\>**.  
  
11. In the Actions pane, expand the **Adaptor Providers** drop-down list, and then click **FILE**.  
  
    **To publish and deploy the policy**  
  
12. In Policy Explorer, under the **RouteBasedOnMessageType** policy, right click **Version 1.0 (not saved)**, and then click **Publish**.  
  
13. In Policy Explorer, under the **RouteBasedOnMessageType** policy, right click **Version 1.0 - Published**, and then click **Deploy**.  
  
    **To create an ESB itinerary domain-specific language (DSL) model**  
  
14. In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.  
  
15. In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.  
  
16. In the **Name** box, type **MessageType**, and then click **Add**.  
  
    **To configure the properties of the itinerary**  
  
17. In Visual Studio, click the design surface of **MessageType.itinerary**. In the **MessageType** Properties window, configure the following properties:  
  
    1.  In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.  
  
    2.  In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).  
  
    3.  In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\MessageType**, and then click **Save**.  
  
        > [!NOTE]
        >  This step enables you to export the itinerary as XML to a local file location. Exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application. You will complete this process later in this How-to topic.  
  
    **To define the structure of the itinerary**  
  
18. From the Toolbox, drag an **On-Ramp** model element to the design surface. In the **OnRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ReceiveOrders**.  
  
    2.  In the **Extender** drop-down list, click **On-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.  
  
    4.  In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.  
  
19. From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **BreRoute**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.  
  
        > [!NOTE]
        >  This property defines that the process will take place in a pipeline (messaging). Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.  
  
    3.  In the **Container** drop-down list, expand **ReceiveOrders**, and then click **Receive Handlers**.  
  
    4.  In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.  
  
20. Right-click the **Resolver** collection of the **BreRoute** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ByMessageType**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Bre Resolver Extension**.  
  
    3.  In the **Policy** drop-down list, click **RouteBasedOnMessageType v 1.0**.  
  
21. In the Toolbox, click **Connector**. Drag a connection from the **ReceiveOrders** model element to the **BreRoute** model element.  
  
22. From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **BreRoute** model element. In the **OffRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendBasedOnType**.  
  
    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
    4.  In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.  
  
23. From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **BreRoute** model element and the **SendBasedOnType** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendPortFilter**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **SendBasedOnType**, and then click **Send Handlers**.  
  
24. In the Toolbox, click **Connector**. Drag a connection from the **BreRoute** model element to the **SendPortFilter** model element.  
  
25. In the Toolbox, click **Connector**. Drag a connection from the **SendPortFilter** model element to the **SendBasedOnType** model element.  
  
    **To export the model for use with the Itinerary Test Client**  
  
26. In Visual Studio, right-click the design surface of the **MessageType** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The XML version of the itinerary opens in Visual Studio.  
  
27. Save all project artifacts.  
  
28. In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (MessageType.xml).  
  
    **To test the itinerary**  
  
29. Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).  
  
30. In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.  
  
31. In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries. Select **MessageType.xml**, and then click **Open** to load the itinerary.  
  
32. Click **OK** to clear the **Itinerary Loaded Successfully** message.  
  
33. In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.  
  
34. In the **Select XML Document to load** dialog box, browse to C:\HowTos. Select **NAOrderDoc.xml**, and then click **Open** to load the test message.  
  
35. Click the **Submit Request** button. When the test completes, click **OK** to dismiss the confirmation that appears.  
  
36. In Windows Explorer, browse to C:\HowTos\Out\\. Verify that the NorthAmerica%MessageID%.xml message has been written to the directory.  
  
## Additional Resources  
 For more information, see the following related topics:  
  
-   [How to: Select an Itinerary Using a Business Rules Policy](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [How to: Implement Content-Based Routing Using a Business Rules Policy for a Known Message Type](../esb-toolkit/apply-content-based-routing-using-business-rules-policy-for-known-message-type.md)  
  
-   [Development Activities](../esb-toolkit/development-activities.md)  
  
-   [Message Routing Patterns](../esb-toolkit/message-routing-patterns.md)  
  
-   [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md)