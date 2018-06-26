---
title: "How to: Validate a Message Using an ESB On-Ramp | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43dfc791-7cb6-45a4-898f-f53def199c08
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Validate a Message Using an ESB On-Ramp
## Goal  
 This section demonstrates how to configure the ESB Dispatcher Disassemble pipeline component to perform message validation for XML messages submitted to an ESB on-ramp.  
  
 In this How-to topic, you will complete the following steps:  
  
-   Create an ESB on-ramp that uses the **ItinerarySelectReceiveXml** pipeline.  
  
-   Configure the ESB Dispatcher Disassemble pipeline component to validate message content.  
  
-   Configure the Itinerary Selector pipeline component to resolve the appropriate itinerary.  
  
-   Test message validation using a valid message and an invalid message.  
  
## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## Before You Begin  
 Complete the following tasks before you perform the steps later in this How-to topic:  
  
- Create an invalid test message.  
  
- Create an ESB itinerary domain-specific language (DSL) model.  
  
- Configure the properties of the itinerary.  
  
- Define the structure of the itinerary.  
  
- Export the model to the Itinerary database.  
  
  The following procedures describe how to do each of these.  
  
#### To create an invalid test message  
  
1.  In Windows Explorer, browse to C:\HowTos.  
  
2.  Create a copy of NAOrderDoc.xml, and then rename the copy Invalid.xml.  
  
3.  In Notepad, open Invalid.xml.  
  
4.  Change **\<ns0:requestType\>10\</ns0:requestType\> to \<ns0:requestType\>TEN\</ns0:requestType\>**.  
  
5.  Save Invalid.xml as UTF-8, and then close Notepad.  
  
    > [!NOTE]
    >  By changing the numerical value of this element to text, the message will no longer be valid according to the schema.  
  
#### To create an ESB itinerary DSL model  
  
1.  In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.  
  
2.  In Solution Explorer, right-click **ItineraryLibrary**, point to **Add**, and then click **New Itinerary**.  
  
3.  In the **Add New Item** dialog box, type **Validation** in the **Name** box, and then click **Add**.  
  
#### To configure the properties of the itinerary  
  
1.  In Visual Studio, click the design surface of **Validation.itinerary**. In the **Validation** Properties window, configure the following properties:  
  
    1.  In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.  
  
    2.  Click the ellipsis button (...) next to the **Itinerary Database** property.  
  
    3.  In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).  
  
2.  In the **Itinerary Status** drop-down list, click **Deployed**.  
  
    > [!NOTE]
    >  This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when the message is received. You will later configure the Itinerary Selector pipeline component to use a static resolver to select the appropriate itinerary from this repository.  
  
#### To define the structure of the itinerary  
  
1.  From the Toolbox, drag an **On-Ramp** model element to the design surface. In the **OnRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ReceiveNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **On-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.  
  
    4.  In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.  
  
2.  From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the existing model element. In the **OffRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendNAOrder**.  
  
    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.  
  
    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
    4.  In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.  
  
3.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendPortFilter**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.  
  
4.  Right-click the **Resolver** collection of the **SendPortFilter** element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ConfigureOffRamp**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transport Name** drop-down list, click **FILE**.  
  
    4.  Click the **Transport Location** property, and then type **C:\HowTos\Out\Validated%MessageID%.xml**.  
  
5.  In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the **SendPortFilter** model element.  
  
6.  In the Toolbox, click **Connector**. Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.  
  
#### To export the model to the itinerary database  
  
1.  In Visual Studio, right-click the design surface of the **Validation** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector pipeline component.  
  
2.  Save all project artifacts.  
  
## Steps  
  
#### To create and configure an ESB on-ramp  
  
1.  Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **BizTalk Server Administration**.  
  
2.  In the BizTalk Server Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand **Microsoft.Practices.ESB**.  
  
3.  Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.  
  
4.  In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.  
  
5.  In the **Receive Location Properties** dialog box, type **OnRamp.Itinerary.HowTo** in the **Name** box.  
  
6.  In the **Type** drop-down list, click **FILE**, and then click **Configure**.  
  
7.  In the **FILE Transport Properties** dialog box, type **C:\HowTos\DropFolder** in the **Receive folder** box, and then click **OK**.  
  
#### To configure the on-ramp to perform message validation  
  
1.  In the **Receive Location Properties** dialog box, in the **Receive pipeline** drop-down list, click **ItinerarySelectReceiveXml**, and then click the ellipsis button (...).  
  
2.  Use the **Configure Pipeline** dialog box to configure the following **XML disassembler** component properties:  
  
    1.  Expand the GlobalBank.Esb application, and then click **Schemas**. Right-click **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**, and then click **Properties**. Copy the **Name** and **Assembly** properties and paste them into a text file.  
  
    2.  In the **Disassemble** component, click **True** in the **ValidateDocument** drop-down list.  
  
    3.  Click the **DocumentSpecNames** property, and then type the fully qualified name of the schema. The fully qualified name starts with the name and is followed by a comma and the assembly information extracted in step a. The following is an example:  
  
         GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc, GlobalBank.ESB.DynamicResolution.Schemas, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c2c8b2b87f54180a  
  
        > [!NOTE]
        >  This is the fully qualified name of the schema to be validated; it is comprised of the schema name and four assembly properties: assembly name, version, culture, and public key token. Multiple values are allowed; separate multiple schemas with a pipe (&#124;) symbol.  
  
#### To configure the Itinerary Selector Pipeline component  
  
1.  In the **Configure Pipeline** dialog box, configure the following **Itinerary Selector** component properties:  
  
    1.  Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.  
  
    2.  Click the **ResolverConnectionString** property, and then type **ITINERARY:\\\name=Validation;**.  
  
    3.  Click **OK** to close the **Configure Pipeline** dialog box.  
  
2.  Click **OK** to close the **Receive Location Properties** dialog box.  
  
3.  In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Enable**.  
  
#### To test the message validation and itinerary selection  
  
1.  In Windows Explorer, browse to C:\HowTos.  
  
2.  Copy (do not move) NAOrderDoc.xml to the DropFolder folder.  
  
3.  Browse to C:\HowTos\Out. Verify that Validated%MessageID%.xml has been written to the directory.  
  
    > [!NOTE]
    >  The valid message completed its itinerary-based routing, as expected.  
  
4.  Delete Validated%MessageID%.xml from the Out folder.  
  
5.  In Windows Explorer, browse to C:\HowTos.  
  
6.  Copy (do not move) Invalid.xml to the DropFolder folder.  
  
7.  Browse to C:\HowTos\Out. Verify that no new message has been delivered.  
  
    > [!NOTE]
    >  The message could not be validated; therefore, itinerary-based routing could not be completed.  
  
8.  Click **Start** on the taskbar, point to **Administrative Tools**, and then click **Event Viewer**.  
  
9. In Event Viewer, expand **Windows Logs**, and then click **Application**.  
  
10. Locate a recent event where the **Source** is **BizTalk Server**, and the **Event ID** is **5719**.  
  
    > [!NOTE]
    >  The submission and failure of the invalid message resulted in an exception entry to the application event log.  
  
11. In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Disable**.  
  
12. After the **OnRamp.Itinerary.HowTo** receive location is disabled, right-click it, and then click **Delete**. In the **Confirm delete receive location** dialog box, click **Yes**.  
  
## Additional Resources  
 For more information, see the following related topics:  
  
-   [How to: Select an Itinerary Using a Business Rules Policy](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [Development Activities](../esb-toolkit/development-activities.md)  
  
-   [Installing and Running the Dynamic Resolution Sample](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)