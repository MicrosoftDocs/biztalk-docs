---
title: "How to: Implement Content-Based Routing Using Message Context Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 952af792-5762-4b04-9087-980bb3323568
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Implement Content-Based Routing Using Message Context Properties
## Goal  
 This section demonstrates how to use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Itinerary Designer to create an itinerary that selects a message recipient based on the message context property and then routes a message to that recipient using the Itinerary Broker messaging service.  
  
 In this topic, you will complete the following steps:  
  
-   Create an itinerary with an itinerary broker and two routing services with static resolvers.  
  
-   Test the itinerary using the Itinerary Test Client sample application.  
  
> [!NOTE]
>  No orchestration-based broker service is provided in the current implementation.  
  
## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## Steps  
  
#### To create an ESB Itinerary DSL model  
  
1.  In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.  
  
2.  In Solution Explorer, right-click **ItineraryLibrary**, point to **Add**, and then click **New Itinerary**.  
  
3.  In the **Add New Item** dialog box, click **ItineraryDsl** in the Templates pane.  
  
4.  In the **Name** box, type **ChoiceRouter**, and then click **Add**.  
  
#### To configure the properties of the itinerary  
  
1.  In Visual Studio, click the design surface of the **ChoiceRouter** itinerary. In the **ChoiceRouter** Properties window, configure the following properties:  
  
    1.  In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.  
  
    2.  In the **Extender Settings** section, click the ellipsis button (...) next to the **Itinerary XML file** property.  
  
    3.  In the **Export Mode** property drop-down list, click **Strict**.  
  
    4.  In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\ChoiceRouter** in the **File name** box, and then click **Save**.  
  
    > [!NOTE]
    >  This step enables you to export the itinerary as XML to a local file location. By exporting an itinerary to a local file location, instead of to the itinerary database, you can test the itinerary using the ESB Test Client application. You will complete this process later in this How-to topic.  
  
#### To define the structure of the itinerary  
  
1.  From the Toolbox, drag an **On-Ramp** model element to the design surface. In the OnRamp1 Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ReceiveNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **On-Ramp Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.  
  
    4.  In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.  
  
2.  From the Toolbox, drag an **Itinerary Broker Service** model element to the designer surface, and then place it to the right side of the **On-Ramp** model element. In the **ItineraryBrokerService1**, configure the following properties:  
  
    1.  Click the **Name** property, and then type **RouteBrokerService**.  
  
    2.  In the **Extender** drop-down list, click **Messaging Broker Extender**.  
  
    3.  In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.  
  
    4.  In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Itinerary.Services.Broker.MessagingBroker**.  
  
3.  Right-click the **Filter** collection, and then click **Add new Filter**. In the **Filter1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ASMXFilter**.  
  
    2.  Click the **Filter** Implementation drop-down list, and then click **XPath Filter**.  
  
    3.  Click the **Expression** property, and then type **count(/ContextProperties/Property[@name='InboundTransportLocation'][contains(., 'ProcessItinerary.asmx')]) > 0**.  
  
4.  Right-click the **Filter** collection, and then click **Add new Filter**. In the **Filter1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **WCFFilter**.  
  
    2.  Click the **Filter Implementation** drop-down list, and click **XPath Filter**.  
  
    3.  Click the **Expression** property, and then type **count(/ContextProperties/Property[@name='InboundTransportLocation'][contains(., 'ESB.ItineraryServices.WCF')]) > 0**.  
  
5.  Right-click the **Resolver** collection of the **RouteBrokerService** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ResolverBrokerRoute**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **MessageContext Resolver Extension**.  
  
6.  In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the **RouteBrokerService** model element.  
  
7.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it under the **RouteBrokerService** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **RouteToFileFromASMX**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.  
  
        > [!NOTE]
        >  This property defines that the process will take place in a pipeline (messaging). Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.  
  
    3.  In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.  
  
    4.  In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.  
  
8.  Right-click the **Resolver** collection of the **RouteToFileFromASMX** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ResolverFromAsmx**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transport Name** drop-down list, click **FILE**.  
  
    4.  Click the **Transport Location** property, and then type **c:\howtos\out\asmx%MessageId%.xml**.  
  
9. From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteToFileFromASMX** model element. In the **OffRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendASMXOrder**.  
  
    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
    4.  In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.  
  
10. From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteToFileFromASMX** model element and the **SendASMXOrder** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendPortFilterASMX**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **SendASMXOrder**, and then click **Send Handlers**.  
  
11. In the Toolbox, click **Connector**. Drag a connection from the **RouteToFileFromASMX** model element to the **SendPortFilterASMX** model element.  
  
12. In the Toolbox, click **Connector**. Drag a connection from the **SendPortFilterASMX** model element to the **SendASMXOrder** model element.  
  
13. From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of **RouteBrokerService** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **RouteToFileFromWCF**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.  
  
        > [!NOTE]
        >  This property defines that the process will take place in a pipeline (messaging). Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.  
  
    3.  In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.  
  
    4.  In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.  
  
14. Right-click the **Resolver** collection of the **RouteToFileFromWCF** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ResolverFromWCF**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transport Name** drop-down list, click **FILE**.  
  
    4.  Click the **Transport Location** property, and then type **c:\howtos\out\wcf%MessageId%.xml**.  
  
15. From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteToFileFromWCF** model element. In the **OffRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendWCFOrder**.  
  
    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
    4.  In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.  
  
16. From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteToFileFromWCF** model element and the **SendWCFOrder** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendPortFilterWCF**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **SendWCFOrder**, and then click **Send Handlers**.  
  
17. In the Toolbox, click **Connector**. Drag a connection from the **RouteToFileFromWCF** model element to the **SendPortFilterWCF** model element.  
  
18. In the Toolbox, click **Connector**. Drag a connection from the **SendPortFilterWCF** model element to the **SendWCFOrder** model element.  
  
19. From the Toolbox, drag an **Itinerary Outport** model element to right border of **RouteBrokerService**. In the **ItineraryBrokerOutPort1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **WCF Port**.  
  
    2.  In the **Filter** drop-down list, click **WCFFilter**.  
  
    3.  In the **Resolver** drop-down list, click **ResolverBrokerRoute**.  
  
20. From the Toolbox, drag an **Itinerary Outport** model element to the bottom border of **RouteBrokerService**. In the **ItineraryBrokerOutPort1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ASMX Port**.  
  
    2.  In the **Filter** drop-down list, click **ASMXFilter**.  
  
    3.  In the **Resolver** drop-down list, click **ResolverBrokerRoute**.  
  
21. In the Toolbox, click **Connector**. Drag a connection from the **WCF Port** model element to the **RouteToFileFromWCF** model element.  
  
22. In the Toolbox, click **Connector**. Drag a connection from the **ASMX Port** model element to the **RouteToFileFromASMX** model element.  
  
#### To export the model for use with the Itinerary Test Client  
  
> [!NOTE]
>  You will need to export the itinerary twice: one time in XML and one time to the database to test the routing through the broker.  
  
1.  In Visual Studio, right-click the design surface of the **ChoiceRouter** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The XML version of the itinerary opens in Visual Studio.  
  
2.  In Windows Explorer, browse to C:\HowTos\Itineraries, and then notice the creation of your itinerary XML (ChoiceRouter.xml).  
  
3.  In Visual Studio, right-click the design surface of the **ChoiceRouter** itinerary, and then click **Export Model**.  
  
4.  In the Properties window, click **Database Itinerary Exporter** in the **Model Exporter** drop-down list.  
  
5.  In the Properties window, set the **Itinerary Database** property connection string to point to the itinerary database.  
  
6.  In the **Itinerary Status** property drop-down list select **Deployed**.  
  
7.  In Visual Studio, right-click the design surface of the **ChoiceRouter** itinerary, and then click **Export Model**.  
  
#### To test the itinerary  
  
1.  Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).  
  
2.  In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.  
  
3.  In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries. Select **ChoiceRouter.xml**, and then click **Open** to load the itinerary.  
  
4.  Click **OK** to close the "Itinerary Loaded Successfully" message.  
  
5.  In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.  
  
6.  In the **Select XML Document to load** dialog box, browse to C:\Patterns\HowTos. Select NAOrderDoc.xml, and then click **Open** to load the test message.  
  
7.  Click the **Submit Request** button. When the test completes, click **OK** to close the confirmation message that appears.  
  
8.  In Windows Explorer, browse to C:\HowTos\Out. Verify that the ASMX%MessageID%.xml messages have been written to this directory.  
  
9. Click the Itinerary Test client **Use WCF Service** check box. In the **Itinerary Name** box, type **ChoiceRouter**, and then click the **Submit Request** button. When the test completes, click **OK** to close the confirmation message.  
  
10. In Windows Explorer, browse to C:\HowTos\Out. Verify that the WCF%MessageID%.xml messages have been written to this directory.  
  
## Additional Resources  
 For more information, see the following related topics:  
  
-   [How to: Select an Itinerary Using a Business Rules Policy](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [How to: Dynamically Route a Message Based on Message Context Using a Business Rules Policy](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
-   [Development Activities](../esb-toolkit/development-activities.md)  
  
-   [Message Routing Patterns](../esb-toolkit/message-routing-patterns.md)