---
title: "How to: Implement Content-Based Routing Using a Business Rules Policy for a Known Message Type | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44451c85-929a-4d13-b0dd-53ea600d0859
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Implement Content-Based Routing Using a Business Rules Policy for a Known Message Type
## Goal  
 This section demonstrates how to create an itinerary that dynamically routes a message, based on the content of a known message type (schema deployed to the Microsoft BizTalk Server Configuration database), using a business rules policy.  
  
 In this How-to topic, you will complete the following steps:  
  
-   Create a business rules policy that will be used to route a message based on content.  
  
-   Create an itinerary routing slip with a BRE resolver to dynamically route a message.  
  
-   Test the itinerary using the Itinerary Test Client sample application.  
  
## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## Before You Begin  
 Complete the following tasks before you perform the steps later in this How-to topic:  
  
- Create the GlobalBank West test message.  
  
- Create the GlobalBank East test message.  
  
  The following procedures describe how to do each of these.  
  
#### To create the GlobalBank West test message  
  
1.  In Windows Explorer, browse to C:\HowTos.  
  
2.  Create a copy of NAOrderDoc.xml, and then name the copy West.xml.  
  
3.  In Notepad, open West.xml, and then change the value of the **customerName** element to **GlobalBankWest**.  
  
4.  Save West.xml as UTF-8, and then close Notepad.  
  
#### To create the GlobalBank East test message  
  
1.  In Windows Explorer, browse to C:\HowTos.  
  
2.  Create a copy of NAOrderDoc.xml, and then name the copy East.xml.  
  
3.  In Notepad, open East.xml, and then change the value of the **customerName** element to **GlobalBankEast**.  
  
4.  Save East.xml as UTF-8, and then close Notepad.  
  
## Steps  
  
#### To create a BRE policy to route using custom message properties  
 This rule will use the customer's name to dynamically set the endpoint used to route the message.  
  
1.  Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **Business Rule Composer**.  
  
2.  In Policy Explorer, right-click **Policies**, and then click **Add New Policy**. Name the policy **RouteBasedOnCustomerKnownType**.  
  
#### To add a routing rule for customer GlobalBank West  
  
1. In the **RouteBasedOnCustomerKnownType** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**. Name the rule **SetWestEndpoint**.  
  
2. In Facts Explorer, click the **XML Schemas** tab, right-click **Schemas**, and then click **Browse**.  
  
3. In the **Schema Files** dialog box, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas, select **NAOrderDoc.xsd**, and then click **Open**.  
  
   > [!NOTE]
   >  This is the schema that defines the NAOrderDoc.xml message, which was used to create the West and East messages you will use for testing.  
  
4. In Facts Explorer, click **NAOrderDoc.xsd**, and then in the Properties pane, click the **Document Type** property, and then type **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.  
  
   > [!NOTE]
   >  This is the fully qualified name of the schema.  
  
5. In Facts Explorer, expand **NAOrderDoc.xsd**, and then expand **OrderDoc**.  
  
6. In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.  
  
7. From Facts Explorer, drag the **customerName** element to the **argument1** node under **Conditions**.  
  
8. Click the **argument2** node, and then type **GlobalBankWest**.  
  
9. In Facts Explorer, click the **Vocabularies** tab, expand **ESB.EndPointInfo**, and then expand **Version 1.0**.  
  
   > [!NOTE]
   >  The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes several vocabularies that can be used for creating rules for use in the ESB. Some of these should be replaced or augmented with your own vocabularies. For example, the **DynamicRunTimeMaptypes** has definitions for the maps provided in the **GlobalBank** samples.  
  
10. From Facts Explorer, drag the **Set End Point Outbound Transport Location** definition to **Actions**.  
  
11. Click **\<empty string\>** and then type **C:\HowTos\Out\West%MessageID%.xml**.  
  
12. From Facts Explorer, drag the **Set End Point Outbound Transport Type** definition to **Actions**.  
  
13. In Facts Explorer, expand **ESB.TransportTypes**, expand **Version 1.0**, and then drag the **Adaptor Providers** definition to **\<empty string\>**.  
  
14. In the **Actions** pane, expand the **Adaptor Providers** drop-down list, and then click **FILE**.  
  
#### To add a routing rule for customer GlobalBank East  
  
1.  In Policy Explorer, right-click the **SetWestEndpoint** rule, and then click **Copy**.  
  
2.  Right-click **Version 1.0 (not saved)**, and then click **Paste**.  
  
3.  In the **New Rule Name** dialog box, type **SetEastEndpoint**, and then click **OK**.  
  
4.  In Policy Explorer, click the **SetEastEndpoint** rule.  
  
5.  In the **Conditions** section, right-click **GlobalBankWest**, and then click **Reset argument**.  
  
6.  Click **argument2**, and then type **GlobalBankEast**.  
  
7.  In the **Actions** section, right-click **C:\HowTos\Out\West%MessageID%.xml**, and then click **Reset argument**.  
  
8.  Click **\<empty string\>**, and then type **C:\HowTos\Out\East%MessageID%.xml**.  
  
#### To add a routing rule for unknown customers  
  
1.  In the RouteBasedOnCustomerKnownType policy, right-click Version 1.0 (not saved), and then click Add New Rule. Name the rule SetUnknownCustomerEndpoint.  
  
2.  In the Rule window, right-click Conditions, and then click Add logical AND.  
  
3.  In the Rule window, right-click AND, point to Predicates, and then click NotEqual.  
  
4.  In Facts Explorer, click the XML Schemas tab, expand NAOrderDoc.xsd, and then expand OrderDoc.  
  
5.  From Facts Explorer, drag the customerName element to the argument1 node under Conditions.  
  
6.  Click the argument2 node, and then type GlobalBankWest.  
  
7.  In the Rule window, right-click AND, point to Predicates, and then click NotEqual.  
  
8.  From Facts Explorer, drag the customerName element to the argument1 node under Conditions.  
  
9. Click the argument2 node, and then type GlobalBankEast.  
  
10. In Facts Explorer, click the Vocabularies tab, expand ESB.EndPointInfo, and then expand Version 1.0.  
  
11. From Facts Explorer, drag the Set End Point Outbound Transport Location definition to Actions.  
  
12. Click \<empty string\>, and then type C:\HowTos\Out\CustomerUnknown%MessageID%.xml.  
  
13. From Facts Explorer, drag the Set End Point Outbound Transport Type definition to Actions.  
  
14. In Facts Explorer, expand ESB.TransportTypes, expand Version 1.0, and then drag the Adaptor Providers definition to \<empty string\>.  
  
15. In the Actions pane, expand the Adaptor Providers drop-down list, and then click FILE.  
  
#### To publish and deploy the policy  
  
1.  In Policy Explorer, under the **RouteBasedOnCustomerKnownType** policy, right click **Version 1.0 (not saved)**, and then click **Publish**.  
  
2.  In Policy Explorer, under the **RouteBasedOnCustomerKnownType** policy, right click **Version 1.0 - Published**, and then click **Deploy**.  
  
#### To create an ESB itinerary DSL model  
  
1.  In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.  
  
2.  In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.  
  
3.  In the **Add New Item** dialog box, in the **Name** box, type **CbrKnownType**, and then click **Add**.  
  
#### To configure the properties of the itinerary  
  
1.  In Visual Studio, click the design surface of **CbrKnownType.itinerary**. In the **CbrKnownType** Properties window, configure the following properties:  
  
    1.  In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.  
  
    2.  In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).  
  
    3.  In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\CbrKnownType** in the **File name** box, and then click **Save**.  
  
        > [!NOTE]
        >  This step enables you to export the itinerary as XML to a local file location. By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application. You will complete this process later in this How-to topic.  
  
#### To define the structure of the itinerary  
  
1.  From the Toolbox, drag an **On-Ramp** model element to the design surface. In the **OnRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ReceiveNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **On-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.  
  
    4.  In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.  
  
2.  From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element. In the **OffRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendRegionalOrders**.  
  
    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
    4.  In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.  
  
3.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendRegionalOrders** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendPortFilter**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **SendRegionalOrders**, and then click **Send Handlers**.  
  
4.  Right-click the **Resolver** collection of the **SendPortFilter** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **RouteRegionalOrders**.  
  
    2.  In the **Transport Name** drop-down list, click **BRE**.  
  
    3.  In the **Resolver Implementation** drop-down list, click **Bre Resolver Extension**.  
  
    4.  In the **Policy** drop-down list, click **RouteBasedOnCustomerKnownType**.  
  
    5.  In the **Recognize Message Format** drop-down list click **True**.  
  
    6.  In the **UseMsg** drop-down list, click **True**.  
  
        > [!NOTE]
        >  If you use the BRE Resolver Extension from orchestration, the **recognizeMessageFormat** property must be set to **False**.  
  
5.  In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the **SendPortFilter** model element.  
  
6.  In the Toolbox, click **Connector**. Drag a connection from the **SendPortFilter** model element to the **SendRegionalOrders** model element.  
  
#### To export the model for use with the Itinerary Test Client  
  
1.  In Visual Studio, right-click the design surface of the **CbrKnownType** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The XML version of the itinerary opens in Visual Studio.  
  
2.  Save all project artifacts.  
  
3.  In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (CbrKnownType.xml).  
  
#### To test the itinerary and business rules  
  
1.  Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).  
  
2.  In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.  
  
3.  In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries. Select **CbrKnownType.xml**, and then click **Open** to load the itinerary.  
  
4.  Click **OK** to clear the **Itinerary Loaded Successfully** message.  
  
5.  In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.  
  
6.  In the **Select XML Document to load** dialog box, browse to C:\HowTos. Select **West.xml**, and then click **Open** to load the test message.  
  
7.  Click the **Submit Request** button. When the test completes, click **OK** to dismiss the confirmation that appears.  
  
8.  In Windows Explorer, browse to C:\HowTos\Out. Verify that the West%MessageID%.xml message has been written to the directory.  
  
9. Repeat the test process using the East.xml message.  
  
10. In Windows Explorer, browse to C:\HowTos\Out. Verify that the East%MessageID%.xml message has been written to the directory.  
  
11. Repeat the test process using the NAOrderDoc.xml message.  
  
12. In Windows Explorer, browse to C:\HowTos\Out. Verify that the CustomerUnknown%MessageID%.xml message has been written to the directory.  
  
## Additional Resources  
 For more information, see the following related topics:  
  
-   [How to: Select an Itinerary Using a Business Rules Policy](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [How to: Dynamically Route a Message Based on Message Context Using a Business Rules Policy](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
-   [Development Activities](../esb-toolkit/development-activities.md)  
  
-   [Message Routing Patterns](../esb-toolkit/message-routing-patterns.md)