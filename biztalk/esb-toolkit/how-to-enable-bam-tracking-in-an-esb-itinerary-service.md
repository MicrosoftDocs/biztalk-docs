---
title: "How to: Enable BAM Tracking in an ESB Itinerary Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58859937-f8d0-4c33-9a7a-62fec8441936
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Enable BAM Tracking in an ESB Itinerary Service
## Goal  
 This section demonstrates how to enable Business Activity Monitor (BAM) tracking for an existing itinerary.  
  
 In this How-to topic, you will complete the following steps:  
  
-   Enable the property used for tracking Itinerary Services using Business Activity Monitor.  
  
-   Test BAM tracking using the Itinerary Test Client sample application.  
  
-   Verify the BAM results using a SQL query.  
  
## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## Before You Begin  
 Complete the following tasks before you perform the steps later in this How-to topic:  
  
- Create an ESB itinerary domain-specific language (DSL) model.  
  
- Configure the properties of the itinerary.  
  
- Define the structure of the itinerary.  
  
  The following procedures describe how to do each of these.  
  
#### To create an ESB itinerary DSL model  
  
1.  In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.  
  
2.  In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.  
  
3.  In the **Add New Item** dialog box, click  **ItineraryDsl** in the Templates pane.  
  
4.  In the **Name** box, type **BamTracking**, and then click **Add**.  
  
#### To configure the properties of the itinerary  
  
1.  In Visual Studio, click the design surface of **BamTracking.itinerary**. In the **BamTracking** Properties window, configure the following properties:  
  
    1.  In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.  
  
    2.  In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).  
  
    3.  In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\BamTracking** and then click **Save**.  
  
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
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Messaging Itinerary Service Extension**.  
  
        > [!NOTE]
        >  This property defines that the process will take place in a pipeline (messaging). Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Itinerary Service Extension**.  
  
    3.  In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.  
  
    4.  In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.  
  
3.  Right-click the **Resolver** collection of the **MapNAOrderToCNOrder** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **StaticallySpecifyTheMap**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.  
  
    4.  In the **TransportName** drop-down list, click **FILE**.  
  
4.  In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the **MapNAOrderToCNOrder** model element.  
  
5.  From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **MapNAOrderToCNOrder** model element. In the **OffRamp1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendCNOrder**.  
  
    2.  In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.  
  
    3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
    4.  In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.  
  
6.  From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **MapNAOrderToCNOrder** model element and the **SendCNOrder** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendPortFilter**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **SendCNOrder**, and then click **Send Handlers**.  
  
7.  Right-click the **Resolver** collection of the **SendPortFilter** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **ConfigureFolderSettings**.  
  
    2.  In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.  
  
    3.  In the **Transport Name** drop-down list, click **FILE**.  
  
    4.  Click the **Transport Location** property, and then type **C:\HowTos\Out\BAM%MessageID%.xml**  
  
        > [!NOTE]
        >  Each off-ramp will have an itinerary service associated with it; the combination of the itinerary service properties and the properties of the off-ramp define the subscription of the dynamic send port.  
  
8.  In the Toolbox, click **Connector**. Drag a connection from the **MapNAOrderToCNOrder** model element to the **SendPortFilter** model element.  
  
9. In the Toolbox, click **Connector**. Drag a connection from the **SendPortFilter** model element to the **SendCNOrder** model element.  
  
10. Save all project artifacts.  
  
## Steps  
  
#### To modify the itinerary  
  
1.  In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.  
  
2.  In Solution Explorer, double-click **BamTracking.itinerary**.  
  
3.  Click the **MapNAOrderToCNOrder** itinerary service element.  
  
4.  In the **MapNAOrderToCNOrder** Properties window, click **True** in the **Tracking Enabled** drop-down list.  
  
5.  Click the **SendPortFilter** itinerary service element.  
  
6.  In the **SendPortFilter** Properties window, click **True** in the **Tracking Enabled** drop-down list.  
  
#### To export the model for use with the Itinerary Test Client  
  
1.  In Visual Studio, right-click the design surface of the **BamTracking** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The XML version of the itinerary opens in Visual Studio.  
  
2.  Save all project artifacts.  
  
3.  In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (BamTracking.xml).  
  
#### To test the itinerary  
  
1.  Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).  
  
2.  In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.  
  
3.  In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries. Select **BamTracking.xml**, and then click **Open** to load the itinerary.  
  
4.  Click **OK** to clear the **Itinerary Loaded Successfully** message.  
  
5.  In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.  
  
6.  In the **Select XML Document to load** dialog box, browse to C:\HowTos. Select **NAOrderDoc.xml**, and then click **Open** to load the test message.  
  
7.  Click the **Submit Request** button. When the test completes, click **OK** to dismiss the confirmation that appears.  
  
8.  In Windows Explorer, browse to C:\HowTos\Out. Verify that the BAM%MessageID%.xml message has been written to the directory.  
  
#### To verify message tracking  
  
1. Click **Start** on the taskbar, point to **All Programs**, point to [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)], and then click **SQL Server Management Studio**.  
  
2. Click **New Query**.  
  
3. In the query pane, type the following:  
  
   ```  
   SELECT *  
   FROM [BAMPrimaryImport].[dbo].[bam_ItineraryServiceActivity_Completed]  
   GO  
   ```  
  
4. Click **Execute**.  
  
5. In the Results pane, use the **TimeStamp** column to locate the most recent entry.  
  
## Additional Resources  
 For more information, see the following related topics:  
  
-   [Development Activities](../esb-toolkit/development-activities.md)  
  
-   [Message Routing Patterns](../esb-toolkit/message-routing-patterns.md)  
  
-   [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md)