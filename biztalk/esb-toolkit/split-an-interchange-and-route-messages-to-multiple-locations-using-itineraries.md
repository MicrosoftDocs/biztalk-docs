---
title: "How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ccd46bee-e4a1-4846-8bde-b0460bda1e72
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries
## Goal  
 This section demonstrates how to create an ESB on-ramp that uses the **ItinerarySelectReceiveXml** pipeline and how to configure the pipeline's components to split an inbound interchange and select the appropriate routing slip for each resulting message, based on message context. Itinerary selection will be resolved using a business rules policy, and messages will be routed differently based on the region in which the customer resides.  
  
 In this How-to topic, you will complete the following steps:  
  
-   Create an ESB on-ramp that splits an XML interchange.  
  
-   Configure the Itinerary Selector pipeline component to use a business rules policy to select the appropriate itinerary.  
  
## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## Before You Begin  
 Complete the following tasks before you perform the steps later in this How-to topic:  
  
-   Create the required artifacts.  
  
-   Add a schemas project to the Patterns solution.  
  
-   Add the artifacts to the Schemas project.  
  
-   Create a BRE policy to select an itinerary using custom message properties.  
  
-   Add a selection rule for customer GlobalBank West.  
  
-   Add a selection rule for customer GlobalBank East.  
  
-   Publish and deploy the policy.  
  
-   Create an ESB itinerary domain-specific language (DSL) model for GlobalBank West messages.  
  
-   Configure the properties of the GlobalBank West itinerary.  
  
-   Define the structure of the GlobalBank West itinerary.  
  
-   Export the GlobalBank West model to the itinerary database.  
  
-   Create an ESB itinerary DSL model for GlobalBank East messages.  
  
-   Configure the properties of the GlobalBank East itinerary.  
  
-   Define the structure of the GlobalBank East itinerary.  
  
-   Export the GlobalBank East model to the itinerary database.  
  
     The following procedures describe how to do each of these.  
  
#### To create the required artifacts  
  
1.  In Windows Explorer, browse to C:\HowTos.  
  
2.  Create a new text document named OrderDocEnvelope.xsd.  
  
3.  Open the OrderDocEnvelope.xsd schema in Notepad.  
  
4.  Edit the document using the following code.  
  
    ```  
    <?xml version="1.0" ?>  
    <xs:schema xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://ESB.BizUnit.Map.Test" targetNamespace="http://ESB.BizUnit.Map.Test" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
      <xs:import schemaLocation="GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc" namespace="http://globalbank.esb.dynamicresolution.com/northamericanservices/" />  
      <xs:annotation>  
        <xs:appinfo>  
          <b:schemaInfo is_envelope="yes" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" />  
          <b:references>  
            <b:reference targetNamespace="http://globalbank.esb.dynamicresolution.com/northamericanservices/" />  
          </b:references>  
        </xs:appinfo>  
      </xs:annotation>  
      <xs:element name="OrderEnvelope">  
        <xs:annotation>  
          <xs:appinfo>  
            <b:recordInfo body_xpath="/*[local-name()='OrderEnvelope' and namespace-uri()='http://ESB.BizUnit.Map.Test']" />  
          </xs:appinfo>  
        </xs:annotation>  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element ref="ns0:OrderDoc" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
5.  Save OrderDocEnvelope.xsd as UTF-8, and then close Notepad.  
  
6.  In the C:\HowTos folder, create a new text document named Batch.xml.  
  
7.  In Notepad, open Batch.xml.  
  
8.  Edit the document using the following code.  
  
    ```  
    <?xml version="1.0" ?>  
    <ns0:OrderEnvelope xmlns:ns0="http://ESB.BizUnit.Map.Test">  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankWest</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>10</ns0:requestType>  
      </ns0:OrderDoc>  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankEast</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>11</ns0:requestType>  
      </ns0:OrderDoc>  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankEast</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>12</ns0:requestType>  
      </ns0:OrderDoc>  
    </ns0:OrderEnvelope>  
    ```  
  
9. Save and close Batch.xml.  
  
#### To add a schemas project to the Patterns solution  
  
1.  In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.  
  
2.  In Solution Explorer, right-click **Solution 'Patterns'**, point to **Add**, and then click **New Project**.  
  
3.  In the **Add New Project** dialog box, in the Project types pane, click **BizTalk Projects**, and then do the following:  
  
    1.  In the Templates pane, click **Empty BizTalk Server Project**.  
  
    2.  In the **Name** box, type **Patterns.Schemas**, and then click **OK**.  
  
4.  In Solution Explorer, right-click **Patterns.Schemas**, and then click **Properties**.  
  
5.  In the Properties window, on the **Signing** tab, select the **Sign the assembly** check box.  
  
6.  In the **Choose a strong name key file** drop-down list, click **\<New...\>**.  
  
7.  In the **Create Strong Name Key** dialog box, configure the following properties:  
  
    1.  In the **Key file name** box, type **Splitting**.  
  
    2.  Clear the **Protect my key file with a password** check box, and then click **OK**.  
  
8.  In the Properties window, on the **Deployment** tab, in the **Application Name** box, type **Microsoft.Practices.ESB**.  
  
9. Close the Properties window.  
  
#### To add the artifacts to the Schemas project  
  
1.  In Solution Explorer, right-click **Patterns.Schemas**, and then click **Add Reference**.  
  
2.  On the **Browse** tab of the **Add Reference** dialog box, browse to and select C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas\bin\Debug\GlobalBank.ESB.DynamicResolution.Schemas.dll, and then click **OK**.  
  
3.  In Solution Explorer, right-click **Patterns.Schemas**, point to **Add**, and then click **Existing Item**.  
  
4.  In the **Add Existing Item** dialog box, browse to and select C:\HowTos\OrderDocEnvelope.xsd, and then click **Add**.  
  
5.  Save all solution artifacts.  
  
6.  In Solution Explorer, right-click **Patterns.Schemas**, and then click **Deploy**.  
  
    > [!NOTE]
    >  This How-to topic uses the same business rules policy and itineraries as those created in the [How to: Select an Itinerary Using a Business Rules Policy](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md) topic. If you have not already completed that section, please complete the following additional steps. If you have completed that section, continue directly to the "Steps" section.  
  
#### To create a Business Rules Engine (BRE) policy to select an itinerary using custom message properties  
  
1.  Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **Business Rule Composer**.  
  
2.  In Policy Explorer, right-click **Policies**, and then click **Add New Policy**. Name the policy **ResolveItineraryBasedOnCustomer**.  
  
#### To add a selection rule for customer GlobalBank West  
  
1.  In the **ResolveItineraryBasedOnCustomer** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**. Name the rule **SetGlobalBankWestItinerary**.  
  
2.  In Facts Explorer, click the **XML Schemas** tab, right-click **Schemas**, and then click **Browse**.  
  
3.  In the **Schema Files** dialog box, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas, select NAOrderDoc.xsd, and then click **Open**.  
  
    > [!NOTE]
    >  This is the schema that defines the NAOrderDoc.xml message, which was used to create the West and East messages you will use for testing.  
  
4.  In Facts Explorer, click NAOrderDoc.xsd, click the **Document Type** property in the Properties pane, and then type **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.  
  
    > [!NOTE]
    >  This is the fully qualified name of the schema.  
  
5.  In Facts Explorer, expand **NAOrderDoc.xsd**, and then expand **OrderDoc**.  
  
6.  In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.  
  
7.  From Facts Explorer, drag the **customerName** element to the **argument1** node under **Conditions**.  
  
8.  Click the **argument2** node, and then type **GlobalBankWest**.  
  
9. In Facts Explorer, click the **Vocabularies** tab. Expand the **ESB.Itinerary** vocabulary, expand **Version 1.1**, and then drag the **Set Itinerary Name** definition to **Actions**.  
  
10. Click **\<empty string\>** and then type **GlobalBankWestItinerary**.  
  
    > [!NOTE]
    >  Later in this How-to topic, you will create this itinerary to process messages from GlobalBank West.  
  
#### To add a selection rule for customer GlobalBank East  
  
1.  In Policy Explorer, right-click the **SetGlobalBankWestItinerary** rule, and then click **Copy**.  
  
2.  Right-click **Version 1.0 (not saved)**, and then click **Paste**.  
  
3.  In the **New Rule Name** dialog box, type **SetGlobalBankEastItinerary**, and then click **OK**.  
  
4.  In Policy Explorer, click the **SetGlobalBankEastItinerary** rule.  
  
5.  In the **Conditions** section, right-click **GlobalBankWest**, and then click **Reset argument**.  
  
6.  Click **argument2**, and then type **GlobalBankEast**.  
  
7.  In the **Actions** section, right-click **GlobalBankWestItinerary**, and then click **Reset argument**.  
  
8.  Click **\<empty string\>** and then type **GlobalBankEastItinerary.**  
  
    > [!NOTE]
    >  Later in this How-to topic, you will create this itinerary to process messages from GlobalBank East.  
  
#### To publish and deploy the policy  
  
1.  In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, click **Version 1.0 (not saved)**, and then click **Publish**.  
  
2.  In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, click **Version 1.0 - Published**, and then click **Deploy**.  
  
#### To create an ESB itinerary DSL model for GlobalBank West messages  
  
1.  In **Visual Studio**, open C:\HowTos\Patterns\Patterns.sln.  
  
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
    >  This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when messages are received. You will later configure the Itinerary Selector pipeline component to use the BRI resolver to evaluate inbound messages and select the appropriate itinerary from this repository.  
  
#### To define the structure of the GlobalBank West itinerary  
  
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
  
3.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element. In the **ItineraryService1** properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **RouteMessage**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.  
  
4.  Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **StaticResolver**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transport Name** drop-down list, click **FILE**.  
  
    4.  Click the **Transport Location** property, and then type **C:\HowTos\Out\West%MessageID%.xml**.  
  
5.  In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the  **RouteMessage** model element.  
  
6.  In the Toolbox, click **Connector**. Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.  
  
#### To export the GlobalBank West model to the itinerary database  
  
1.  In Visual Studio, right-click the design surface of the **GlobalBankWestItinerary** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.  
  
2.  Save all project artifacts.  
  
#### To create an ESB itinerary DSL model for GlobalBank East message  
  
1.  In **Visual Studio**, open C:\HowTos\Patterns.sln.  
  
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
  
#### To define the structure of the GlobalBank East itinerary  
  
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
  
#### To export the GlobalBank East model to the itinerary database  
  
1.  In Visual Studio, right-click the design surface of the **GlobalBankEastItinerary** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.  
  
2.  Save all project artifacts.  
  
## Steps  
  
#### To create and configure an ESB on-ramp  
  
1.  Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **BizTalk Server Administration**.  
  
2.  In the BizTalk Server Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand **Microsoft.Practices.ESB**.  
  
3.  Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.  
  
4.  In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.  
  
5.  In the **Receive Location Properties** dialog box, in the **Name** box, type **OnRamp.Itinerary.HowTo**.  
  
6.  In the **Type** drop-down list, click **FILE,** and then click **Configure**.  
  
7.  In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type **C:\HowTos\DropFolder**, and then click **OK**.  
  
#### To configure the Itinerary Selector pipeline component  
  
1.  In the **Receive Location Properties** dialog box, click **ItinerarySelectReceiveXml** in the **Receive pipeline** drop-down list, and then click the ellipsis button (...).  
  
2.  Use the **Configure Pipeline** dialog box to configure the following **Itinerary Selector** component properties:  
  
    1.  Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.  
  
    2.  Click the **ResolverConnectionString** property, and then type **BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**  
  
    3.  Click **OK** to close the **Configure Pipeline** dialog box.  
  
        > [!NOTE]
        >  Because this receive location is disassembling an XML interchange, no XML Disassembler component configuration is required.  
  
3.  Click **OK** to close the **Receive Location Properties** dialog box.  
  
4.  In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Enable**.  
  
#### To test the Itinerary Selector and business rules  
  
1.  In Windows Explorer, browse to C:\HowTos.  
  
2.  Copy (do not move) Batch.xml to the DropFolder folder.  
  
3.  Browse to C:\HowTos\Out. Verify that one West%MessageID%.xml message and two East%MessageID%.xml messages have been written to the directory.  
  
    > [!NOTE]
    >  Although the messages are identical except for the value of the customer element, they were processed using different itineraries, based on the resolution of the Itinerary Selector pipeline component.  
  
4.  In the BizTalk Server Administration Console, right-click the OnRamp.Itinerary.HowTo receive location, and then click Disable.  
  
5.  After the **OnRamp.Itinerary.HowTo** receive location is disabled, right-click it, and then click **Delete**. In the **Confirm delete receive location** dialog box, click **Yes**.  
  
## Additional Resources  
 For more information, see the following related topics:  
  
-   [How to: Select an Itinerary Using a Business Rules Policy](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [Development Activities](../esb-toolkit/development-activities.md)  
  
-   [Installing and Running the Dynamic Resolution Sample](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [Message Routing Patterns](../esb-toolkit/message-routing-patterns.md)