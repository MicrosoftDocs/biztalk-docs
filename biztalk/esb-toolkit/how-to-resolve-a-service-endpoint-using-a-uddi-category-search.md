---
description: "Learn more about: How to: Resolve a Service Endpoint Using a UDDI Category Search"
title: "Resolve a Service Endpoint Using a UDDI Category Search"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to: Resolve a Service Endpoint Using a UDDI Category Search
## Goal  
 This section demonstrates how to use the ESB Designer domain-specific language (DSL) to create an itinerary-based routing slip that uses the Universal Description, Discovery, and Integration (UDDI) 3 resolver to locate a service endpoint using a category search. In this scenario, the service endpoint will be a file endpoint published in UDDI.  
  
 In this How-to topic, you will complete the following steps:  
  
-   Create an itinerary routing slip to resolve a service endpoint.  
  
-   Configure the itinerary to route the message to a service endpoint using a UDDI 3 resolver.  
  
-   Test the itinerary using the Itinerary Test Client sample application.  
  
## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## Steps  
  
#### To create an itinerary model  
  
1.  In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.  
  
2.  In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.  
  
3.  In the **Add New Item** dialog box, type **UDDI3CategorySearch** in the **Name** box, and then click **Add**.  
  
#### To configure the properties of the itinerary  
  
1.  In Visual Studio, click the design surface of **UDDI3CategorySearch.itinerary**. In the **UDDI3CategorySearch** Properties window, configure the following properties:  
  
    1.  In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.  
  
    2.  Under the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).  
  
    3.  In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\UDDI3CategorySearch** in the **File name** box, and then click **Save**.  
  
        > [!NOTE]
        >  This step enables you to export the itinerary as XML to a local file location. By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application. You will complete this process later in this How-to topic.  
  
#### To define the structure of the itinerary  
  
1.  From the Toolbox, drag an **On-Ramp** model element to the design surface. In the **OnRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ReceiveNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **On-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.  
  
    4.  In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.  
  
2.  From the Toolbox, drag an **Itinerary Service** model element to the design surface. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **CategoryRoute**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.  
  
    3.  In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.  
  
    4.  In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**  
  
3.  Right-click the **Resolver** collection of the **CategoryRoute** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **CategorySearch**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Uddi3 Resolver Extension**.  
  
    3.  In the **Resolver Moniker** drop-down list, click **UDDI3**.  
  
    4.  Click the **Category Search** property, and then click the ellipsis button (…).  
  
    5.  In the **Name Value Property Editor** dialog box, click **Add**.  
  
    6.  Click the **Name** property, and then type **uddi:esb:biztalkapplication**.  
  
    7.  Click the **Value** property, and then type **GlobalBank.ESB**.  
  
    8.  In the **Name Value Property Editor** dialog box, click **Add**.  
  
    9. Click the **Name** property, and then type **uddi:esb:portname**.  
  
    10. Click the **Value** property, and then type **OrderFileServicev3**.  
  
    11. In the **Name Value Property Editor** dialog box, click **Add**.  
  
    12. Click the **Name** property, and then type **uddi:esb:version**.  
  
    13. Click the **Value** property, and then type **1**.  
  
    14. Click **OK** to close the **Name Value Property Editor** dialog box.  
  
4.  Right-click the **CategorySearch** resolver, and then click **Test Resolver Configuration**.  
  
    > [!NOTE]
    >  Verify the output displayed in the Output window.  
  
5.  In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the **CategoryRoute** model element.  
  
6.  From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **CategoryRoute** model element. In the **OffRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
    4.  In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.  
  
7.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **CategoryRoute** model element and the **SendNAOrder** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendPortFilter**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.  
  
8.  In the Toolbox, click **Connector**. Drag a connection from the **CategoryRoute** model element to the **SendPortFilter** model element.  
  
9. In the Toolbox, click **Connector**. Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.  
  
#### To export the model for use with the Itinerary Test Client  
  
1.  In Visual Studio, right-click the design surface of the **UDDI3CategorySearch** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The XML version of the itinerary opens in Visual Studio.  
  
2.  Save all project artifacts.  
  
3.  In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (UDDI3CategorySearch.xml).  
  
#### To test the itinerary  
  
1.  Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).  
  
2.  In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.  
  
3.  In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries. Select **UDDI3CategorySearch.xml**, and then click **Open** to load the itinerary.  
  
4.  Click **OK** to clear the **Itinerary Loaded Successfully** message.  
  
5.  In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.  
  
6.  In the **Select XML Document to load** dialog box, browse to C:\HowTos. Select NAOrderDoc.xml, and then click **Open** to load the test message.  
  
7.  Click the **Submit Request** button. When the test completes, click **OK** to dismiss the confirmation that appears.  
  
8.  In Windows Explorer, browse to **C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out** and verify that the **%MessageID%.xml** message has been written to the directory.  
  
## Additional Resources  
 For more information, see the following related topics:  
  
-   [How to: Resolve a Service Endpoint Using a UDDI Binding Key Search](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  
  
-   [Development Activities](../esb-toolkit/development-activities.md)  
  
-   [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md)
