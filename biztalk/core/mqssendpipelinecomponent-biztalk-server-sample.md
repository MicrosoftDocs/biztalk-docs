---
title: "MQSSendPipelineComponent (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "examples, MQSeries adapters"
  - "pipelines, examples"
  - "MQSeries adapters, examples"
  - "examples, pipelines"
ms.assetid: ac709e45-524b-45ab-9673-060790ecbed2
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MQSSendPipelineComponent (BizTalk Server Sample)
This sample demonstrates how to write a pipeline component that reads a set of MQSeries property values from an XML file and applies them to a message.  
  
## What This Sample Does  
 This sample is composed of two [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects, a pipeline component project and a pipeline project that makes use of the pipeline component.  
  
## Where to Find This Sample  
  
- *\<SamplesPath\>*\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyComponent  
  
- *\<SamplesPath\>*\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyPipeline  
  
  The following table shows the files in this sample and describes their purpose.  
  
|                                                                              **File**                                                                               |                                         **Description**                                          |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.sln,<br /><br /> SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.csproj |                    The project and solution files for the pipeline component.                    |
|                                              SetMQSeriesHeaderPropertyComponent\CSetMQSeriesHeaderPropertyComponent.cs                                              |                      The Visual C#® source file for the pipeline component.                      |
|                                                      SetMQSeriesHeaderPropertyComponent\SetMQSMQMDHdrProps.xml                                                      |                 The MQSeries properties read and used by the pipeline component.                 |
|   SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btproj,<br /><br /> SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.sln   |                     The project and solution files for the BizTalk pipeline.                     |
|                                               SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.snk                                               |                   The strong naming key file for the BizTalk pipeline project.                   |
|                                               SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btp                                               | The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline. |
  
## How to Use This Sample  
 To create the application, you must complete the following steps:  
  
1. Create the folders for the application.  
  
2. Modify and compile the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for the pipeline component.  
  
3. Copy the compiled assembly and the header file to the appropriate folders.  
  
4. Modify the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline.  
  
5. Compile and deploy the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline project.  
  
6. Set up a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location.  
  
7. Create a MQSeries queue.  
  
8. Set up a send port.  
  
9. Enable the receive location and start the send port.  
  
## Creating the Folders for the Application  
 This procedure creates the appropriate folders for the application.  
  
#### To create the folders for the application  
  
1.  Create a folder named **temp** on your C:\ drive if it does not already exist.  
  
2.  Create a folder under the **C:\temp** directory named **Pickup3**.  
  
## Modifying and Compiling the Project for the Pipeline Component  
 This procedure modifies and compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for the pipeline component.  
  
#### To modify and compile the project for the pipeline component  
  
1. Double-click the solution file, **SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.sln** to open the solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2. Double-click the class file **CSetMQSeriesHeaderPropertyComponent.cs** to open the class file in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
3. Locate the variable **samplesDir**, verify that this variable is set to the location **C:\temp**.  
  
4. Right-click the solution in the Solution Explorer and click **Build**. This will compile the project into a dll located in the **SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent\bin\Debug\\** directory.  
  
## Copying the Assembly and Header File to Appropriate Folders  
 This procedure copies the compiled assembly and the header file to the appropriate folders.  
  
#### To copy the compiled assembly and header file to the appropriate folders  
  
1. Copy the compiled assembly **SetMQSeriesHeaderPropertyComponent.dll** to the BizTalk pipeline components folder. The default location for the BizTalk pipeline components folder is [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Pipeline Components.  
  
2. Copy the MQHeader properties file **SetMQSMQMDHdrProps.xml** to the **C:\temp** directory.  
  
## Modifying the Project for the BizTalk Server Pipeline  
 This procedure modifies the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline.  
  
#### To modify the project for the BizTalk Server pipeline  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution by double-clicking the solution file, **SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.sln**.  
  
2. Create a strong name key file for the project. To do that, do the following:  
  
   1. Open a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command prompt.  
  
   2. Change directories to \<SamplesPath\>\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent.  
  
   3. Type the following:  
  
       `sn -k MQSSendPipelineComponent.snk`  
  
   4. Press ENTER. This will create the key file.  
  
3. In **Solution Explorer**, right-click the project and click **Properties** to launch Project Designer for the project (in the center window).  
  
   1.  In the Project Designer, click **Signing** tab.  
  
   2.  In the right-hand pane, select the **Sign the assembly** option..  
  
   3.  Click drop-down list for the **Choose a strong name key file** option, and click **Browse**.  
  
   4.  Browse to \<SamplesPath\>\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\MQSSendPipelineComponent.snk, click **Open**.  
  
4. The pipeline component that you created earlier is already added to the **Pre-Assemble** stage of this pipeline project. If this component was not already added you would need to complete the following steps to add it:  
  
   1. In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] IDE, click the **Toolbox** tab on the left side.  
  
   2. Right-click the **Toolbox**, and click **Choose Items**.  
  
   3. In the **Choose Toolbox Items** dialog box, click the **BizTalk Pipeline Components** tab, select the **Custom Component to Set MQseries header properties**component, and then click **OK**.  
  
   4. Drag the **Custom Component to Set MQseries header properties**component to the **Pre-Assemble** stage of this pipeline.  
  
## Compiling and Deploying the Pipeline Project  
 This procedure compiles and deploys the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline project.  
  
#### To compile and deploy the pipeline project  
  
1.  In the Solution Explorer window, right-click the solution, and then click **Deploy Solution**. This builds the solution and deploys the assembly to the BizTalk Management database.  
  
2.  Verify the Assembly was deployed to the BizTalk Management database:  
  
    1.  Open the BizTalk Administration Console.  
  
    2.  Click to expand **BizTalk Group [\<servername\>:\<management database\>]**, and then click to expand the **Assemblies** folder.  
  
         The deployed pipeline assembly should be visible under the **Assemblies** folder.  
  
## Creating the Receive Location  
 This procedure creates a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location.  
  
#### To create the receive location  
  
1.  In the BizTalk Server Administration Console, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  
  
2.  In the **One-way Receive Port Properties** dialog box, in the **Name** box type "MQReply" and click **OK**.  
  
3.  In the left pane, click **Receive Locations** tab, and then click **New**.  
  
4.  In the **Receive Location Properties** dialog box, in the **Name** field, type "ReceiveFile".  
  
5.  In the **Transport Type** box, select **FILE**.  
  
6.  In the **Receive Handler** field, select **BizTalkServerApplication**.  
  
7.  In the **Receive pipeline** field, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.  
  
8.  In the **Receive folder** field, type "C:\temp\Pickup3".  
  
9. In the **File mask** field, type "*.\*".  
  
10. Click **OK**, and then click **OK** again to exit the **Receive Location Properties** dialog box.  
  
## Creating a MQSeries Queue Through the MQSeries Explorer  
 If you have the required permissions to the MQSeries Server for Windows installation, you can create the MQSeries queue through the adapter dialog boxes, and can skip this next procedure.  
  
 If you do not have such access, you can use the following procedure to create the queue using the IBM WebSphere MQ Explorer.  
  
#### To create a MQSeries queue through the MQSeries Explorer  
  
1.  Click **Start**, point to **Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.  
  
2.  Double-click **Queue Managers**, and then double-click the default queue manager. The default queue manager is typically named **QM_**\<*machine_name*\> where *machine_name* is the name of your computer.  
  
3.  Right-click **Queues**, point to **New**, and then click **Local Queue**.  
  
4.  In **Create Local Queue** dialog box, in **Queue Name**, type **SETHEADER**, and then click **OK**.  
  
## Creating the Send Port and MQSeries Queue  
 This procedure creates the send port for the output message. The MQSeries queue is also created when you create the send port if you have not already created it.  
  
#### To create the send port and MQSeries queue  
  
1.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
2.  In the **Send Port Properties** dialog box, in the **Name** box, type "MQSolicitResponse".  
  
3.  In the **Transport Type** box, select **MQSeries**.  
  
4.  In the **Send pipeline** box, select **SetMQSeriesHeaderPropertyPipeline.SetMQSeriesHeadersSendPipeline**.  
  
5.  In **Filters**, add a new entry with the following name/value pairs:  
  
    -   Set **Property** to "BTS.ReceivePortName".  
  
    -   Set **Operator** to "==".  
  
    -   Set **Value** to "ReceiveFile".  
  
        > [!NOTE]
        >  This sets the send port to subscribe to messages that arrive on the ReceiveFile receive port.  
  
6.  Click **Transport**.  
  
7.  In the **Address (URI)** field, click the ellipsis (…) button.  
  
8.  In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** field, click the ellipsis (…) button.  
  
9. In the **Queue Definition** dialog box, in the **Server Name** field, type your computer name.  
  
10. In the **Queue Manager** field, select the default queue manager.  
  
11. In the Queue field, type "SETHEADER", and then click **Export**.  
  
12. In the **Export** dialog box, click **Create Queue**, and then click **OK** or **Done** until you have exited all dialog.  
  
## Enabling the Receive Location and Starting the Send Port  
 This procedure enables the receive location and start the send port.  
  
#### To enable the receive location and start the send port  
  
1.  In the BizTalk Server Administration console, click **Receive Ports**.  
  
2.  In the details pane, right-click the **MQIn** receive location and click **Enable**.  
  
3.  In the details pane, right-click the **SetMQHeader** send port and click **Start**.  
  
## Testing the Application  
 This procedure tests the application.  
  
#### To test the application  
  
1.  Put a file into the **C:\Temp\Pickup3** folder.  
  
2.  Launch the WebSphere MQ Explorer and double-click the SETHEADER queue to examine the message(s) in the SETHEADER queue.  
  
     To see all of the context properties for the messages in the SETHEADER queue, complete the following steps:  
  
    1.  Double-click the **SETHEADER** queue to display the **Message Browser** dialog box.  
  
    2.  In the **Message Browser** dialog box, click **Columns** to display the **Show/Hide Columns for Messages** dialog box.  
  
    3.  Under **Available Columns**, double-click each entry to make it visible in the **Message Browser** dialog box, and then click **OK**.  
  
3.  The message context properties for each message should be visible in the **Message Browser** dialog box.  
  
## See Also  
 [MQSeries Adapter Samples](../core/mqseries-adapter-samples.md)