---
title: "How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c27749ba-c228-4cd4-827e-e8009a0c999d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip
## Goal  
 This section demonstrates how to use the ESB Designer domain-specific language (DSL) to create an itinerary that implements message transformation by invoking a BizTalk map, and then it routes the messages using the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] FILE adapter.  
  
 In this How-to topic, you will complete the following steps:  
  
-   Create an itinerary routing slip with a transform itinerary service that implements a BizTalk map.  
  
-   Configure the itinerary to route the transformed message to a file location.  
  
-   Test the itinerary using the Itinerary Test Client sample application.  
  
## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## Steps  
  
#### To create an ESB itinerary DSL model  
  
1.  In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.  
  
2.  In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.  
  
3.  In the **Add New Item** dialog box, click **ItineraryDsl** in the Templates pane.  
  
4.  In the **Name** box, type **DataModelTransformation**, and then click **Add**.  
  
#### To configure the properties of the itinerary  
  
1.  In Visual Studio, click the design surface of **DataModelTransformation.itinerary**. In the **DataModelTransformation** Properties window, configure the following properties:  
  
    1.  In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.  
  
    2.  In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).  
  
    3.  In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\DataModelTransformation**, and then click **Save**.  
  
        > [!NOTE]
        >  This step enables you to export the itinerary as XML to a local file location. By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application. You will complete this process later in this How-to topic.  
  
#### To define the structure of the itinerary  
  
1.  From the Toolbox, drag an **On-Ramp** model element to the design surface. In the **OnRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ReceiveNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.  
  
    3.  In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.  
  
    4.  In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.  
  
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
  
    4.  In the **Transport Name** drop-down list, click **FILE**.  
  
4.  In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the **MapNAOrderToCNOrder** model element.  
  
5.  From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **MapNAOrderToCNOrder** model element. In the **OffRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendCNOrder**.  
  
    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
    4.  In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.  
  
6.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **MapNAOrderToCNOrder** model element and the **SendCNOrder** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendPortFilter**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **SendCNOrder**, and then click **Send Handlers**.  
  
7.  Right-click the **Resolver** collection of the **SendPortFilter** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ConfigureFolderSettings**.  
  
    2.  In the **Transport Name** drop-down list, click **FILE**.  
  
    3.  Click the **Transport Location** property, and then type **C:\HowTos\Out\\%MessageID%.xml**.  
  
        > [!NOTE]
        >  Each off-ramp will have an Itinerary Service associated with it; the combination of the Itinerary Service properties and the properties of the off-ramp define the subscription of the dynamic send port.  
  
8.  In the Toolbox, click **Connector**. Drag a connection from the **MapNAOrderToCNOrder** model element to the **SendPortFilter** model element.  
  
9. In the Toolbox, click **Connector**. Drag a connection from the **SendPortFilter** model element to the **SendCNOrder** model element.  
  
#### To export the model for use with the Itinerary Test Client  
  
1.  In Visual Studio, right-click the design surface of the **DataModelTransformation** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The XML version of the itinerary opens in Visual Studio.  
  
2.  Save all project artifacts.  
  
3.  In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (DataModelTransformation.xml).  
  
#### To test the itinerary  
  
1.  Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).  
  
2.  In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.  
  
3.  In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries. Select **DataModelTransformation.xml**, and then click **Open** to load the itinerary.  
  
4.  Click **OK** to clear the **Itinerary Loaded Successfully** message.  
  
5.  In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.  
  
6.  In the **Select XML Document to load** dialog box, browse to C:\HowTos. Select **NAOrderDoc.xml**, and then click **Open** to load the test message.  
  
7.  Click the **Submit Request** button. When the test completes, click **OK** to dismiss the confirmation that appears.  
  
8.  In Windows Explorer, browse to C:\HowTos\Out. Verify that the **%MessageID%.xml** message has been written to the directory.  
  
## Additional Resources  
 For more information, see these related topics:  
  
1.  [How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)  
  
2.  [Development Activities](../esb-toolkit/development-activities.md)  
  
3.  [Message Transformation Patterns](../esb-toolkit/message-transformation-patterns.md)