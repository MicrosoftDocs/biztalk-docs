---
title: "How to: Route a Single Message to Multiple Recipients Using an Itinerary Routing Slip | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42c30493-4fe1-4fd5-8bc7-af091535b091
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Route a Single Message to Multiple Recipients Using an Itinerary Routing Slip
## Goal  
 This section demonstrates how to use the Designer domain-specific language (DSL) to create an itinerary that routes a message to three distinct recipients using a static resolver and the [!INCLUDE[prague](../includes/prague-md.md)] FILE adapter.  
  
 In this How-to topic, you will complete the following steps:  
  
-   Create an itinerary with three static resolvers to route messages to multiple recipients.  
  
-   Test the itinerary using the Itinerary Test Client sample application.  
  
## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## Steps  
  
#### To create an ESB itinerary DSL model  
  
1.  In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.  
  
2.  In Solution Explorer, right-click **ItineraryLibrary**, point to **Add**, and then click **New Itinerary**.  
  
3.  In the **Add New Item** dialog box, click **ItineraryDsl** in the Templates pane.  
  
4.  In the **Name** box, type **RecipientList**, and then click **Add**.  
  
#### To configure the properties of the itinerary  
  
1.  In Visual Studio, click the design surface of RecipientList.itinerary. In the RecipientList Properties window, configure the following properties:  
  
    1.  In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.  
  
    2.  In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).  
  
    3.  In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\RecipientList**, and then click **Save**.  
  
        > [!NOTE]
        >  This step enables you to export the itinerary as XML to a local file location. By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application. You will complete this process later in this How-to topic.  
  
#### To define the structure of the itinerary  
  
1.  From the Toolbox, drag an **On-Ramp** model element to the design surface. In the **OnRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ReceiveNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **On-Ramp Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.  
  
    4.  In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.  
  
2.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **RouteToThreeRecipients**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.  
  
        > [!NOTE]
        >  This property defines that the process will take place in a pipeline (messaging). Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.  
  
    3.  In the **Container** drop-down list, expand **ReceiveNaOrderDoc**, and then click **Receive Handlers**.  
  
    4.  In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.  
  
3.  Right-click the **Resolver** collection of the **RouteToThreeRecipients** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **FirstResolver**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transport Name** drop-down list, click **FILE**.  
  
    4.  Click the **Transport Location** property, and then type **C:\HowTos\Out\First%MessageID%.xml**.  
  
        > [!NOTE]
        >  You have added the first of three resolvers for this itinerary service. You will now add two more resolvers to route the message to additional recipients.  
  
4.  Right-click the **Resolver** collection of the **RouteToThreeRecipients** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SecondResolver**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transport Name** drop-down list, click **FILE**.  
  
    4.  Click the **Transport Location** property, and then type **C:\HowTos\Out\Second%MessageID%.xml**.  
  
5.  Right-click the **Resolver** collection of the **RouteToThreeRecipients** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ThirdResolver**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transport Name** drop-down list, click **FILE**.  
  
    4.  Click the **Transport Location** property, and then type **C:\HowTos\Out\Third%MessageID%.xml**.  
  
6.  In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the **RouteToThreeRecipients** model element.  
  
7.  From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteToThreeRecipients** model element. In the **OffRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendThreeMessages**.  
  
    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
    4.  In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.  
  
8.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteToThreeRecipients** model element and the **SendThreeMessages** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendPortFilter**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **SendThreeMessages**, and then click **Send Handlers**.  
  
9. In the Toolbox, click **Connector**. Drag a connection from the **RouteToThreeRecipients** model element to the **SendPortFilter** model element.  
  
10. In the Toolbox, click **Connector**. Drag a connection from the **SendPortFilter** model element to the **SendThreeMessages** model element.  
  
#### To export the model for use with the Itinerary Test Client  
  
1.  In Visual Studio, right-click the design surface of the **RecipientList** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The XML version of the itinerary opens in Visual Studio.  
  
2.  Save all project artifacts.  
  
3.  In Windows Explorer, browse to C:\HowTos\Itineraries, and then notice the creation of your itinerary XML (RecipientList.xml).  
  
#### To test the itinerary  
  
1.  Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).  
  
2.  In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.  
  
3.  In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries. Select **RecipientList.xml**, and then click **Open** to load the itinerary.  
  
4.  Click **OK** to clear the "Itinerary Loaded Successfully: message.  
  
5.  In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.  
  
6.  In the **Select XML Document to load** dialog box, browse to C:\Patterns. Select NAOrderDoc.xml, and then click **Open** to load the test message.  
  
7.  Click the **Submit Request** button. When the test completes, click **OK** to dismiss the confirmation that appears.  
  
8.  In Windows Explorer, browse to C:\HowTos\Out\\. Verify that the following messages have been written to the directory:  
  
    -   First%MessageID%.xml  
  
    -   Second%MessageID%.xml  
  
    -   Third%MessageID%.xml  
  
## Additional Resources  
 For more information, see the following related topics:  
  
-   [Development Activities](../esb-toolkit/development-activities.md)  
  
-   [Message Routing Patterns](../esb-toolkit/message-routing-patterns.md)  
  
-   [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md)