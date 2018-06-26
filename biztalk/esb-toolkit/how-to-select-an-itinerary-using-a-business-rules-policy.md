---
title: "How to: Select an Itinerary Using a Business Rules Policy | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f6373a8-d9d6-46c6-95e3-f62dd33c342a
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Select an Itinerary Using a Business Rules Policy
## Goal  
 This section demonstrates how to create business rules that can be used to select an itinerary based on the content of a received message and how to configure the Itinerary Selector pipeline component within a generic itinerary on-ramp to call these rules. This section describes a business scenario in which messages are routed differently, based on the region in which the customer resides.  
  
 In this How-to topic, you will complete the following steps:  
  
-   Model itineraries for the Western and Eastern divisions of customer Global Bank.  
  
-   Create business rules policies that will be used to select an itinerary for processing request.  
  
-   Configure the Itinerary Selector pipeline component to use a business rules policy to select the appropriate itinerary.  
  
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
  
#### To create a Business Rules Engine (BRE) policy to select an itinerary using custom message properties  
  
1.  Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **Business Rule Composer**.  
  
2.  In Policy Explorer, right-click **Policies**, and then click **Add New Policy**. Name the policy **ResolveItineraryBasedOnCustomer**.  
  
    > [!NOTE]
    >  This How-to topic uses the same business rules policy and itineraries as those created in the topic [How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md). If you have already completed that section, you can skip to the procedure, "To create and configure an ESB on-ramp" later in this topic.  
  
#### To add a selection rule for customer GlobalBank West  
  
1.  In the **ResolveItineraryBasedOnCustomer** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**. Name the rule **SetGlobalBankWestItinerary**.  
  
2.  In Facts Explorer, click the **XML Schemas** tab, right-click **Schemas**, and then click **Browse**.  
  
3.  In the **Schema Files** dialog box, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas, select **NAOrderDoc.xsd**, and then click **Open**.  
  
    > [!NOTE]
    >  This is the schema that defines the NAOrderDoc.xml message, which was used to create the West and East messages you will use for testing.  
  
4.  In Facts Explorer, click **NAOrderDoc.xsd**, click the **Document Type** property in the Properties pane, and then type **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.  
  
    > [!NOTE]
    >  This is the fully qualified name of the schema.  
  
5.  In Facts Explorer, expand **NAOrderDoc.xsd**, and then expand **OrderDoc**.  
  
6.  In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.  
  
7.  From Facts Explorer, drag the **customerName** element to the **argument1** node under **Conditions**.  
  
8.  Click the **argument2** node, and then type **GlobalBankWest**.  
  
9. In Facts Explorer, click the **Vocabularies** tab. Expand the **ESB.Itinerary** vocabulary, expand **Version 1.1**, and then drag the **Set Itinerary Name** definition to **Actions**.  
  
10. Click **\<empty string\>**, and then type **GlobalBankWestItinerary**.  
  
    > [!NOTE]
    >  Later in this How-to topic, you will create this itinerary to process messages from GlobalBank West.  
  
#### To add a selection rule for Customer GlobalBank East  
  
1.  In Policy Explorer, right-click the **SetGlobalBankWestItinerary** rule, and then click **Copy**.  
  
2.  Right-click **Version 1.0 (not saved)**, and then click **Paste**.  
  
3.  In the **New Rule Name** dialog box, type **SetGlobalBankEastItinerary**, and then click **OK**.  
  
4.  In Policy Explorer, click the **SetGlobalBankEastItinerary** rule.  
  
5.  In the **Conditions** section, right-click **GlobalBankWest**, and then click **Reset argument**.  
  
6.  Click **argument2**, and then type **GlobalBankEast**.  
  
7.  In the **Actions** section, right-click **GlobalBankWestItinerary**, and then click **Reset argument**.  
  
8.  Click **\<empty string\>** and then type **GlobalBankEastItinerary**.  
  
    > [!NOTE]
    >  Later in the How-to topic, you will create this itinerary to process messages from GlobalBank East.  
  
#### To publish and deploy the policy  
  
1.  In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, right click **Version 1.0 (not saved)**, and then click **Publish**.  
  
2.  In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, right click **Version 1.0 - Published**, and then click **Deploy**.  
  
#### To create an ESB itinerary domain-specific language (DSL) model for GlobalBank West messages  
  
1.  In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.  
  
2.  In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.  
  
3.  In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.  
  
4.  In the **Name** box, type **GlobalBankWestItinerary**, and then click **Add**.  
  
#### To configure the properties of the GlobalBank West itinerary  
  
1.  In Visual Studio, click the design surface of **GlobalBankWestItinerary.itinerary**. In the **GlobalBankWestItinerary** Properties window, configure the following properties:  
  
    1.  In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.  
  
    2.  Click the ellipsis button (...) next to the **Itinerary Database** property.  
  
    3.  In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).  
  
2.  In the **Itinerary Status** drop-down list, click **Deployed**.  
  
    > [!NOTE]
    >  This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository upon message reception. You will later configure the Itinerary Selector pipeline component to use the Business Rules Engine resolver (BRI) to evaluate inbound messages and select the appropriate itinerary from this repository.  
  
#### To define the structure of the itinerary  
  
1.  From the Toolbox, drag an **On-Ramp** model element to the design surface. In the **OnRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ReceiveNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.  
  
    3.  In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.  
  
    4.  In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.  
  
2.  From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element. In the **OffRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.  
  
    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
    4.  In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.  
  
3.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **RouteMessage**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.  
  
4.  Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **StaticResolver**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transport Name** drop-down list, click **FILE**.  
  
    4.  Click the **Transport Location** property, and then type **C:\HowTos\Out\West%MessageID%.xml**.  
  
5.  In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessage** model element.  
  
6.  In the Toolbox, click **Connector**. Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.  
  
#### To export the model to the itinerary database  
  
1.  In Visual Studio, right-click the design surface of the **GlobalBankWestItinerary** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.  
  
2.  Save all project artifacts.  
  
#### To create an ESB itinerary DSL model for GlobalBank East message  
  
1.  In Visual Studio, open C:\HowTos\Patterns.sln.  
  
2.  In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.  
  
3.  In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.  
  
4.  In the **Name** box, type **GlobalBankEastItinerary**, and then click **Add**.  
  
#### To configure the properties of the GlobalBank East itinerary  
  
1.  In Visual Studio, click the design surface of **GlobalBankEastItinerary.itinerary**. In the **GlobalBankEastItinerary** Properties window, configure the following properties:  
  
    1.  In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.  
  
    2.  Click the ellipsis button (...) next to the **Itinerary Database** property.  
  
    3.  In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).  
  
2.  In the **Itinerary Status** drop-down list, click **Deployed**.  
  
    > [!NOTE]
    >  This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when messages are received. You will later configure the Itinerary Selector pipeline component to use the BRI resolver to evaluate inbound messages and select the appropriate itinerary from this repository.  
  
#### To define the structure of the itinerary  
  
1.  From the Toolbox, drag an **On-Ramp** model element to the design surface. In the **OnRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ReceiveNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.  
  
    3.  In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.  
  
    4.  In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.  
  
2.  From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element. In the **OffRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.  
  
    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
    4.  In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.  
  
3.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **RouteMessage**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.  
  
4.  Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **StaticResolver**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transport Name** drop-down list, click **FILE**.  
  
    4.  Click the **Transport Location** property, and then type **C:\HowTos\Out\East%MessageID%.xml**.  
  
5.  In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessage** model element.  
  
6.  In the Toolbox, click **Connector**. Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.  
  
#### To export the model to the itinerary database  
  
1.  In Visual Studio, right-click the design surface of the **GlobalBankEastItinerary** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.  
  
2.  Save all project artifacts.  
  
#### To create and configure an ESB on-ramp  
  
1.  Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **BizTalk Server Administration**.  
  
2.  In the BizTalk Server Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand **Microsoft.Practices.ESB**.  
  
3.  Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.  
  
4.  In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.  
  
5.  In the **Receive Location Properties** dialog box, in the **Name** box, type **OnRamp.Itinerary.HowTo**.  
  
6.  In the **Type** drop-down list, click **FILE**, and then click **Configure**.  
  
7.  In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type **C:\HowTos\DropFolder**, and then click **OK**.  
  
#### To configure the Itinerary Selector pipeline component  
  
1.  In the **Receive Location Properties** dialog box, in the **Receive pipeline** drop-down list, click **ItinerarySelectReceiveXml**, and then click the ellipsis button (...).  
  
2.  Use the **Configure Pipeline** dialog box to configure the following **Itinerary Selector** component properties:  
  
    1.  Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.  
  
    2.  Click the **ResolverConnectionString** property, and then type **BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**  
  
    3.  Click **OK** to close the **Configure Pipeline** dialog box.  
  
3.  Click **OK** to close the **Receive Location Properties** dialog box.  
  
4.  In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Enable**.  
  
#### To test the itinerary selector and business rules  
  
1.  In Windows Explorer, browse to C:\HowTos.  
  
2.  Copy (do not move) the files East.xml and West.xml to the DropFolder folder.  
  
3.  Browse to C:\HowTos\Out. Verify that the East%MessageID%.xml and West%MessageID%.xml messages have been written to the directory.  
  
    > [!NOTE]
    >  Though identical except for the value of the customer element, the messages were processed using different itineraries, based on the resolution of the Itinerary Selector pipeline component.  
  
4.  In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Disable**.  
  
5.  After the **OnRamp.Itinerary.HowTo** receive location is disabled, right-click it, and then click **Delete**. In the **Confirm delete receive location** dialog box, click **Yes**.  
  
## Additional Resources  
 For more information, see the following related topics:  
  
-   [How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)  
  
-   [Development Activities](../esb-toolkit/development-activities.md)  
  
-   [Installing and Running the Dynamic Resolution Sample](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [Message Routing Patterns](../esb-toolkit/message-routing-patterns.md)