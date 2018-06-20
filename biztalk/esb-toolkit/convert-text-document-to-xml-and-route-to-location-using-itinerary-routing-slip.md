---
title: "How to: Convert a Text Document to XML and Route to a File Location Using an Itinerary Routing Slip | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01597a5f-5ca3-440e-ad97-70332233f319
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Convert a Text Document to XML and Route to a File Location Using an Itinerary Routing Slip
## Goal  
 The section demonstrates how to create a pipeline that will convert a text document to XML and then select the appropriate itinerary and route the message to a FILE location.  
  
 In this How-to topic, you will complete the following steps:  
  
-   Use a pipeline to receive a flat file document and convert it to XML.  
  
-   Configure the Itinerary Selector pipeline component to resolve the appropriate routing slip.  
  
-   Create an on-ramp that uses the custom pipeline.  
  
-   Test itinerary-based routing of a flat file message.  
  
## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## Before You Begin  
 Complete the following tasks before you perform the steps later in this How-to topic:  
  
- Deploy the **DataFormatTransformation** itinerary.  
  
- Create the test message.  
  
  The following procedures describe how to do each of these.  
  
#### To deploy the DataFormatTransformation itinerary  
  
1.  In Visual Studio, open C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation\DataFormatTransformation.sln.  
  
2.  In Solution Explorer, in the **Itinerary.Library** project, double-click **DataFormatTransformation.itinerary** to open it in the Itinerary Designer.  
  
3.  In Visual Studio, click the design surface of **DataFormatTransformation.itinerary**. In the **DataFormatTransformation.itinerary** Properties window, configure the following properties:  
  
    1.  In the **Itinerary Status** drop-down list, click **Deployed**.  
  
    2.  In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.  
  
    3.  Click the ellipsis button (...) next to the **Itinerary Database** property.  
  
    4.  In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).  
  
4.  Save all project artifacts.  
  
5.  In Visual Studio, right-click the design surface of the **DataModelTransformation** itinerary, and then click **Export Model**.  
  
#### To create the receive pipeline  
  
1.  In Visual Studio, right-click **DataFormatTransformation.Schemas**, and then click **Properties**. Click **Application**, and then type **GlobalBank.ESB.DataFormatTransformation.Schemas** in the **Assembly name** box.  
  
2.  Right-click **DataFormatTransformation.Schemas**, and then click **Properties**. Click **Signing**, and then verify that the **Sign the assembly** check box is selected and that the assembly location points to **.\\..\\..\\..\\..\\..\keys\Microsoft.Practices.ESB.snk**.  
  
3.  Right-click **DataFormatTransformation.Pipelines**, and then click **Remove**.  
  
4.  Right-click **DataFormatTransformation**, point to **Add**, and then click **New Project**. Click **Biztalk Projects**, and then click **Empty Biztalk Server Project**. In the **Name** box, type **DataFormatTransformationReceive.Pipeline**.  
  
5.  Right-click **DataFormatTransformationReceive.Pipeline**, and then click **Properties**. Click **Signing**, and then verify that the **Sign the assembly** check box is selected and that the assembly location points to **C:\projects\Microsoft.Practices.ESB\keys\Microsoft.Practices.ESB.snk**.  
  
6.  Right-click **DataFormatTransformationReceive.Pipeline**, point to **Add**, and then click **New Item**.  
  
7.  In the **Add New Item** dialog box, click **Receive Pipeline** in the Templates pane. In the **Name** box, type **ItinerarySelectReceiveFF**, and then click **Add**.  
  
8.  Right-click **References** for the DataFormatTransformationReceive.Pipeline project, and then click **Add Reference**. Click the **Projects** tab, and then click **DataFormatTransformation.Schemas**. Click **OK** to add the reference.  
  
9. From the Toolbox, drag a **Flat file disassembler** pipeline component to the **Disassemble** stage of the pipeline.  
  
10. In the Properties window for the flat file disassemble, click **DataModelTransformation.Schemas.NAOrderDocFF** in the **Document schema** drop-down list.  
  
11. From the Toolbox, drag an **ESB Itinerary Selector** pipeline component to the **Resolve Party** stage of the pipeline.  
  
12. From the Toolbox, drag an **ESB Dispatcher** pipeline component to the **Resolve Party** stage of the pipeline, and then place it under the **ESB Itinerary Selector** pipeline component.  
  
13. Save all project artifacts.  
  
## To create the test message  
  
1.  Click once in the NAOrderDocFF.xsd schema file of the DataFormatTransformation.Schemas project. In the Properties pane of Visual Studio, change the following two properties:  
  
    -   **Generate Instance Output Type**. Click the drop-down list for this property to change it to **Native**.  
  
    -   **Output Instance Filename**. Click the ellipsis button (…) for this property and accept the default path of C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation. In the **File name** box, type **NAOrderDocFF**, and then click **Save**.  
  
2.  Right-click **NAOrderDocFF.xsd** under **DataFormatTransformation.Schemas**, and then click **Generate Instance**. At this point, you should have a new file generated in the C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation directory.  
  
3.  Copy (do not move) the file NAOrderDocFF.txt from C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation to C:\HowTos.  
  
    > [!NOTE]
    >  This is the message you will receive and convert to XML. This document represents a flat file version of North American Order document.  
  
## Steps  
  
#### To deploy the receive pipeline and the schema  
  
1.  Right-click **DataFormatTransformationReceive.Pipeline**, and then click **Properties**. Click **Deployment**, and then type **Microsoft.Practices.ESB** in the **Application Name** box.  
  
2.  Right-click the **DataFormatTransformation.Schemas** project, and then click **Properties**. Click **Deployment**, and then type **Microsoft.Practices.ESB** in the **Application Name** box.  
  
3.  Close the Properties panes for both **DataFormatTransformationReceive.Pipeline** and **DataFormatTransformation.Schemas**.  
  
4.  In Solution Explorer, right-click the **DataFormatTransformation** project, and then click **Deploy Solution**.  
  
#### To create and configure an ESB on-ramp  
  
1.  Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **BizTalk Server Administration**.  
  
2.  In the BizTalk Server Administration Console, expand **BizTalk Group**, expand **Applications**, and then click **Microsoft.Practices.ESB**.  
  
3.  Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.  
  
4.  In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.  
  
5.  In the **Receive Location Properties** dialog box, in the **Name** box, type **OnRamp.Itinerary.FlatFile.FILE**.  
  
6.  In the **Type** drop-down list, click **FILE**, and then click **Configure**.  
  
7.  In the **FILE Transport Properties** dialog box, in the **Receive Folder** box, type **C:\HowTos\DropFolder**.  
  
8.  In the **FILE Transport Properties** dialog box, in the **File mask** box, type **\*.txt**, and then click **OK**.  
  
#### To configure the Itinerary Selector pipeline component  
  
1.  In the **Receive Location Properties** dialog box, click **ItinerarySelectReceiveFF** in the **Receive pipeline** drop down list, and then click the ellipsis button (...).  
  
2.  Use the **Configure Pipeline** dialog box to configure the following **Itinerary Selector** component properties:  
  
    1.  Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.  
  
    2.  Click the **ResolverConnectionString** property, type **ITINERARY:\\\name=DataFormatTransformation;** and then click **OK**.  
  
3.  Click **OK** to close the **Receive Location Properties** dialog box.  
  
4.  In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.FlatFile.FILE** receive location, and then click **Enable**.  
  
#### To test itinerary-based routing of a flat file message  
  
1.  In Windows Explorer, browse to C:\HowTos.  
  
2.  Copy (do not move) NAOrderDocFF.txt to C:\HowTos\DropFolder.  
  
3.  Browse to C:\HowTos\Out. Verify that the DFT%MessageID%.xml message has been written to the directory.  
  
4.  In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.FlatFile.FILE** receive location, and then click **Disable**.  
  
5.  After the **OnRamp.Itinerary.FlatFile.FILE** receive location is disabled, right-click it, and then click **Delete**. In the **Confirm delete receive location** dialog box, click **Yes**.  
  
## Additional Resources  
 For more information, see the following related topics:  
  
-   [How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [How to: Route a Single Message to Multiple Recipients Using an Itinerary Routing Slip](../esb-toolkit/route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip.md)  
  
-   [Development Activities](../esb-toolkit/development-activities.md)  
  
-   [Message Transformation Patterns](../esb-toolkit/message-transformation-patterns.md)