---
title: "How to: Publish a Service to the UDDI 3.0 Registry | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c3bd0ed-e5f1-43eb-98d1-e3247a565ba2
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Publish a Service to the UDDI 3.0 Registry
## Goal  
 This section demonstrates how to use the UDDI Service site to publish a Web service endpoint that can be resolved from within an itinerary for the purpose of routing an ESB message. You will duplicate the existing PurchaseOrderSubmitOrderService service presently published to the registry.  

 In this How-to topic, you will complete the following steps:  

-   Publish a service to the Universal Description, Discovery, and Integration (UDDI) 3 registry using the UDDI Publisher tool.  

-   Test the service publication using an itinerary routing slip that resolves the service endpoint using a UDDI3 resolver.  

## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) and the execution of the UDDI Publisher tool (you can install it at %ESB Install Folder%\Bin\Microsoft.Practices.ESB.UDDIPublisher.exe).  

## Steps  

#### To create the NewPOService in the UDDI registry  

1.  In Internet Explorer, browse to the UDDI Service site (by default, the URL for this is http://localhost/uddi).  

2.  On the **uddi Services** page, click **Publish**.  

3.  In the Publish pane, right-click **Microsoft.Practices.ESB**, and then click **Add Service**.  

4.  On the following page, select **Specify a key to use**, and then click **Continue**.  

5.  On the following page, click the **esb** key partition. In the **Key Suffix** box, type **newposervice**, and then click **Continue**.  

6.  On the following page, next to (**New Service Name**), click **Edit**. Name the service **NewPOService**, and then click **Update**.  

7.  Click **Add Description**, type a description for the service (for example, **Sample Service**), and then click **Update**.  

#### To add a binding for the NewPOService  

1.  Click the **Bindings** tab, and then click **Add Binding**.  

2.  Select **Specify a key to use**, and then click **Continue**.  

3.  On the following page, click the **esb** key partition. In the **Key Suffix** box, type **newposervicebinding**, and then click **Continue**.  

4.  Under **Access Point**, click **Edit**, and then complete the following:  

    1.  In the **Access Point** box, type **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.  

    2.  In the **Use Type** drop-down list, click **endpoint**, and then click **Update**.  

#### To configure the binding instance information  

1. Click the **Instance Info** tab, and then click **Add Instance Info**.  

2. In the **Search for tModel names containing** box, type **%esb%** and then click **Search**.  

3. Locate and click the **tModel** for **transporttype**.  

   > [!NOTE]
   >  To complete the remaining steps in this procedure, you may be required to change between page 1 and page 2.  

4. In the **Descriptions** section, click **Add Description**.  

5. In the **Description** box, type **Transport Type for ESB Itinerary Use**, and then click **Update**.  

6. Click the **Instance Details** tab, and then click **Edit**.  

7. In the **Instance Parameters** box, type **WCF-BasicHttp**, and then click **Update**.  

8. In the **Descriptions** section, click **Add Description**.  

9. In the **Description** box, type **WCF Basic HTTP Transport**, and then click **Update**.  

10. In the Publish pane, under **NewPOService**, click **http://localhost/esb.canadianservices/submitposervice.asmx**.  

11. On the **Instance Info** tab, click **Add Instance Info**.  

12. Using the steps described earlier, add the following instance information, according to the values shown in the following table.  


    |                           tModel                           |       Description        |                          Parameter                           |         Parameter description          |
    |------------------------------------------------------------|--------------------------|--------------------------------------------------------------|----------------------------------------|
    | microsoft-com:esb:runtimeresolution:messageexchangepattern | Message Exchange Pattern |                           Two-Way                            |           Two-way operation            |
    |      microsoft-com:esb:runtimeresolution:cachetimeout      |      Cache Timeout       |                              -1                              |           Currently disabled           |
    |     microsoft-com:esb:runtimeresolution:jaxrpcresponse     |      JaxRpcResponse      |                            false                             |                                        |
    |         microsoft-com:esb:runtimeresolution:action         |      Service Action      |                         submitOrder                          | Specifies the service method to invoke |
    |    microsoft-com:esb:runtimeresolution:targetnamespace     |    Service Namespace     | http://globalbank.esb.dynamicresolution.com/canadianservices |            Target namespace            |

#### To configure the binding categorization  

1.  In the Publish pane, under **NewPOService**, click **http://localhost/esb.canadianservices/submitposervice.asmx**.  

2.  On the **Categories** tab, click **Add Custom Category**.  

3.  In the **Search** box, type **%esb%** and then click **Search**.  

4.  Locate and click the **microsoft-com:esb:runtimeresolution:biztalkapplication** tModel.  

5.  In the **Key Name** box, type **BizTalk Application**.  

6.  In the **Key Value** box, type **Microsoft.Practices.ESB**, and then click **Add Category**.  

7.  Using the steps described earlier, add the following custom categories, according to the values shown in the following table.  

    |tModel|Key name|Key value|  
    |------------|--------------|---------------|  
    |microsoft-com:esb:runtimeresolution:portname|Port Name|NewPOService|  
    |microsoft-com:esb:runtimeresolution:transporttype|Transport Type|WCF-BasicHttp|  

#### To locate the service in the UDDI registry  

1.  In Internet Explorer, on the **uddi Services** page, click **Search**.  

2.  Click the **Services** tab.  

3.  In the **Service Name** box, type **%PO%**, and then click **Search**.  

4.  In the **Search** pane, on the **Results** tab, click **NewPOService**.  

    > [!NOTE]
    >  This confirms the service was successfully published to the registry.  

#### To create an itinerary model to test the UDDI service publication  

1.  In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.  

2.  In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.  

3.  In the **Add New Item** dialog box, in the **Name** box, type **NewBindingKeySearch**, and then click **Add**.  

#### To configure the properties of the itinerary  

1.  In Visual Studio, click the design surface of **NewBindingKeySearch.itinerary**. In the **NewBindingKeySearch** Properties window, configure the following properties:  

    1.  In the **Is Request Response** drop-down list, click **True**.  

    2.  In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.  

    3.  In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).  

    4.  In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\NewBindingKeySearch** in the **File name** box, and then click **Save**.  

        > [!NOTE]
        >  This step enables you to export the itinerary as XML to a local file location. By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application. You will complete this process later in this How-to topic.  

#### To define the structure of the itinerary  

1.  From the Toolbox, drag an **On-Ramp** model element to the design surface. In the **OnRamp1** Properties window, configure the following properties:  

    1.  Click the **Name** property, and then type **ReceiveNAOrder**.  

    2.  In the **Extender** drop-down list, click **On-Ramp ESB Extender**.  

    3.  In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.  

    4.  In the **Receive Port** drop-down list, click **OnRamp.Itinerary.Response**.  

2.  From the Toolbox, drag an **Itinerary Service** model element to the design surface. In the **ItineraryService1** Properties window, configure the following properties:  

    1.  Click the **Name** property, and then type **TransformNAOrder**.  

    2.  In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.  

    3.  In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.  

    4.  In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.  

3.  Right-click the **Resolver** collection of the **TransformNAOrder** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  

    1.  Click the **Name** property, and then type **NAOrder_to_CNOrder**.  

    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  

    3.  In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.  

4.  In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the **TransformNAOrder** model element.  

5.  From the Toolbox, drag an **Itinerary Service** model element to the design surface. In the **ItineraryService1** Properties window, configure the following properties:  

    1.  Click the **Name** property, and then type **BindingKeyRoute**.  

    2.  In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.  

    3.  In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.  

    4.  In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.  

6.  Right-click the **Resolver** collection of the **BindingKeyRoute** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  

    1.  Click the **Name** property, and then type **BindingKeySearch**.  

    2.  In the **Resolver Implementation** drop-down list, click **Uddi3 Resolver Extension**.  

    3.  In the **Resolver Moniker** drop-down list, click **UDDI3**.  

    4.  Click the **Binding key** property, and then type **uddi:esb:newposervicebinding**. To find the key value, click the http://localhost/ESB.CanadianServices/SubmitPOService.asmx service in UDDI, and then click More Details.  

7.  Right-click the **BindingKeySearch** resolver, and then click **Test Resolver Configuration**.  

    > [!NOTE]
    >  Verify the output displayed in the Output window.  

8.  In the Toolbox, click **Connector**. Drag a connection from the **TransformNAOrder** model element to the **BindingKeyRoute** model element.  

9. From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **BindingKeyRoute** model element. In the **OffRamp1** Properties window, configure the following properties:  

    1.  Click the **Name** property, and then type **SendCNOrder**.  

    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.  

    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  

    4.  In the **Send Port** drop-down list, click **DynamicResolutionSolicitResp**.  

10. From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **BindingKeyRoute** model element and the **SendCNOrder** model element. In the **ItineraryService1** Properties window, configure the following properties:  

    1.  Click the **Name** property, and then type **SendPortFilter**.  

    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.  

    3.  In the **Off-Ramp** drop-down list, expand **SendCNOrder**, and then click **Send Handlers**.  

11. In the Toolbox, click **Connector**. Drag a connection from the **BindingKeyRoute** model element to the **SendPortFilter** model element.  

12. In the Toolbox, click **Connector**. Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.  

#### To export the model for use with the Itinerary Test Client  

1.  In Visual Studio, right-click the design surface of the **NewBindingKeySearch** itinerary, and then click **Export Model**.  

    > [!NOTE]
    >  The XML version of the itinerary opens in Visual Studio.  

2.  Save all project artifacts.  

3.  In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (NewBindingKeySearch.xml).  

#### To test the itinerary  

1.  Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).  

2.  In the Itinerary Test Client, in the **Web Service Options** group, clear the **Use WCF Service** box and then select the **Two-Way Service** check box.  

3.  Click the **Load Itinerary** button.  

4.  In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries. Select **NewBindingKeySearch.xml**, and then click **Open** to load the itinerary.  

5.  Click **OK** to clear the **Itinerary Loaded Successfully** message.  

6.  In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.  

7.  In the **Select XML Document to load** dialog box, browse to C:\HowTos. Select **NAOrderDoc.xml**, and then click **Open** to load the test message.  

8.  Click the **Submit Request** button. When the test completes, click **OK** to dismiss the confirmation that appears.  

9. Verify that the correct response message appears in the **Result** text box of the **Itineray Test Client**.  

## Additional Resources  
 For more information, see the following related topics:  

-   [How to: Resolve a Service Endpoint Using a UDDI Binding Key Search](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  

-   [How to: Resolve a Service Endpoint Using a UDDI Category Search](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  

-   [Development Activities](../esb-toolkit/development-activities.md)