---
title: "How to: Transform a Message and Route to a Service Endpoint Using a Request-Response Message Exchange Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1e656fb-6c5f-4b2b-a1b6-4c812b78ee22
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Transform a Message and Route to a Service Endpoint Using a Request-Response Message Exchange Pattern
## Goal  
 This section demonstrates how to use the ESB Designer domain-specific language (DSL) to create a request-response itinerary that can be used with a two-way on-ramp. You will create a routing slip to receive a message, transform the message, submit the message to a service, and return the service response message to the submitter of the original message.  
  
 In this How-to topic, you will complete the following steps:  
  
-   Create an itinerary routing slip with a transform itinerary service that implements a Microsoft BizTalk Server map.  
  
-   Configure the itinerary to route the transformed message to a service endpoint.  
  
-   Configure the itinerary to return the service response message to the original sending party.  
  
-   Test the itinerary using the Itinerary Test Client sample application.  
  
## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## Steps  
  
#### To create an ESB itinerary DSL model  
  
1.  In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.  
  
2.  In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.  
  
3.  In the **Add New Item** dialog box, in the **Name** box, type **RequestResponse**, and then click **Add**.  
  
#### To configure the properties of the itinerary  
  
1.  In Visual Studio, click the design surface of **RequestResponse.itinerary**. In the **RequestResponse** Properties window, configure the following properties:  
  
    1.  In the **Is Request Response** drop-down list, click **True**.  
  
    2.  In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.  
  
    3.  In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).  
  
    4.  In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\RequestResponse**, and then click **Save**.  
  
        > [!NOTE]
        >  This step enables you to export the itinerary as XML to a local file location. By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application. You will complete this process later in this How-to topic.  
  
#### To define the structure of the itinerary  
  
1.  From the Toolbox, drag an **On-Ramp** model element to the design surface. In the **OnRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ReceiveNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **On-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.  
  
    4.  In the **Receive Port** drop-down list, click **OnRamp.Itinerary.Response**.  
  
2.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **MapNAOrderToCNOrder**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.  
  
        > [!NOTE]
        >  This property defines that the process will take place in a pipeline (messaging). Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.  
  
    3.  In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.  
  
    4.  In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.  
  
3.  Right-click the **Resolver** collection of the **MapNAOrderToCNOrder** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **StaticallySpecifyTheMap**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.  
  
4.  In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the **MapNAOrderToCNOrder** model element.  
  
5.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **MapNAOrderToCNOrder** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **RouteToCNService**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.  
  
        > [!NOTE]
        >  This property defines that the process will take place in a pipeline (messaging). Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.  
  
    3.  In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.  
  
    4.  In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.  
  
6.  Right-click the **Resolver** collection of the **RouteToCNService** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **StaticallySpecifyTheService**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transport Name** drop-down list, click **WCF-BasicHttp**.  
  
    4.  Click the **Transport Location** property, and then type **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.  
  
    5.  Click the **Target Namespace** property, and then type **http://globalbank.esb.dynamicresolution.com/canadianservices**.  
  
    6.  Click the **Action** property, and then type **submitOrder**.  
  
7.  In the Toolbox, click **Connector**. Drag a connection from the **MapNAOrderToCNOrder** model element to the **RouteToCNService** model element.  
  
8.  From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteToCNService** model element. In the **OffRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **InvokeCNService**.  
  
    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
    4.  In the **Send Port** drop-down list, click **DynamicResolutionSolicitResp**.  
  
9. From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteToCNService** model element and the **InvokeCNService** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendPortFilter**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **InvokeCNService**, and then click **Send Handlers**.  
  
10. In the Toolbox, click **Connector**. Drag a connection from the **RouteToCNService** model element to the **SendPortFilter** model element.  
  
11. In the Toolbox, click **Connector**. Drag a connection from the **SendPortFilter** model element to the **InvokeCNService** model element.  
  
12. Right-click the design surface, and then click **Validate**.  
  
    > [!NOTE]
    >  The itinerary validates; it is not necessary to connect the off-ramp back to the on-ramp in order to send the response message back to the requesting party. By using a two-way on-ramp, the final message is automatically returned to the requesting party.  
  
#### To export the model for use with the Itinerary Test Client  
  
1.  In Visual Studio, right-click the design surface of the **RequestResponse** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The XML version of the itinerary opens in Visual Studio.  
  
2.  Save all project artifacts.  
  
3.  In Windows Explorer, browse to C:\HowTos\Itineraries. Notice the creation of your itinerary XML (RequestResponse.xml).  
  
#### To test the itinerary  
  
1.  Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).  
  
2.  In the Itinerary Test Client, clear the **Use WCF Service** check box.  
  
3.  In the **Web Service Options** section, select the **Two Way Service** check box, and then click **Load Itinerary**.  
  
4.  In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries. Select **RequestResponse.xml**, and then click **Open** to load the itinerary.  
  
5.  Click **OK** to clear the **Itinerary Loaded Successfully** message.  
  
6.  In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.  
  
7.  In the **Select XML Document to load** dialog box, browse to C:\HowTos. Select **NAOrderDoc.xml**, and then click **Open** to load the test message.  
  
8.  Click the **Submit Request** button. When the test completes, click **OK** to dismiss the confirmation that appears.  
  
9. In the **Results** box, notice the message's root node is **submitOrderResponse** and the default namespace is ... **canadianservices**.  
  
    > [!NOTE]
    >  If the response message requires additional transformation before the response is sent to the requesting party, you must use a pipeline that contains the ESB Forwarder component. For an example of this functionality, see the [Installing and Running the Multiple Web Services Sample](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md).  
  
## Additional Resources  
 For more information, see the following related topics:  
  
-   [How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [Development Activities](../esb-toolkit/development-activities.md)  
  
-   [Message Routing Patterns](../esb-toolkit/message-routing-patterns.md)  
  
-   [Installing and Running the Multiple Web Services Sample](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)