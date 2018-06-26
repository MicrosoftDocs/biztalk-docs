---
title: "File Adapter (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "examples, File adapters"
  - "File adapters, examples"
ms.assetid: d59cecb4-6353-44d5-b8d6-316446758536
caps.latest.revision: 46
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File Adapter (BizTalk Server Sample)
The File Adapter sample is written in Microsoft Visual C# .NET to work with Microsoft BizTalk Server. It provides code to build either a dynamic or a static adapter.  However, the following procedure only outlines the static adapter. A static adapter is an adapter with a static set of schemas and no custom user interface. A dynamic adapter has a custom user interface and potentially a dynamic set of schemas. Both static and dynamic adapters use the Add Adapter Wizard to add their schemas to a BizTalk project.  

> [!NOTE]
>  The File adapter sample is not the same as the native FILE adapter that ships with BizTalk Server. Thus when selecting the transport type in using this sample select "static" instead of FILE.  

 The dynamic adapter with a custom user interface and potentially dynamic set of schemas will require additional code in the adapter management side. To better understand use of the dynamic set of schemas, see [Dynamic Design-Time Adapter Configuration](../core/dynamic-design-time-adapter-configuration.md).  

## What This Sample Does  
 The sample adapter copies files from a file folder, submits to BizTalk as messages, or takes messages from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and drops to a file folder. It provides code to build either a dynamic or a static adapter; however, the following procedure only outlines the static adapter. A static adapter is an adapter with a static set of schemas and no custom user interface. A dynamic adapter has a custom user interface and potentially a dynamic set of schemas. Both static and dynamic adapters use the Add Adapter Wizard to add their schemas to a BizTalk project.  

 You can use the sample file adapter as a template on which to create other custom adapters.  

## Where to Find This Sample  
 \<*Samples Path*\>**\AdaptersDevelopment\File Adapter**  

> [!NOTE]
>  The default location for \<*Samples Path*\> is *%ProgramFiles%*\Microsoft BizTalk Server\SDK\Samples when BizTalk Server is installed on a computer running a 32-bit version of Windows. The default location for \<*Samples Path*\> is *%ProgramFiles(x86)%*\Microsoft BizTalk Server\SDK\Samples when BizTalk Server is installed on a computer running a 64-bit version of Windows. To determine the values associated with the *%ProgramFiles%* or *%ProgramFiles(x86)%* environment variables type **echo %ProgramFiles%** or **echo %ProgramFiles(x86)%** at a command prompt and press ENTER. If running this sample on a 64-bit operating system, you will need to change all references in any of the .reg files from **%ProgramFiles%** to **%ProgramFiles(x86)%** before running the .reg files.  

 The following tables show the files in this sample and describe their purpose.  

|\File Adapter files|Description|  
|--------------------------|-----------------|  
|\BizTalk Project files|Contains the adapter harness project, used to test the sample adapter.|  
|\Design Time files|Contains the design time and management project (AdapterManagement.csproj).|  
|\Runtime files|Contains the run-time file-copy receive and transmit projects (DotNetFile.csproj).|  
|DynamicAdapterManagement.reg|Registers the sample dynamic adapter.|  
|Instance.xml|Sample file to pass through the file adapter.|  
|StaticAdapterManagement.reg|Registers the sample static adapter.|  

|\BizTalk Project\Adapter Harness files|Description|  
|----------------------------------------------|-----------------|  
|AdapterHarness.odx, AdapterHarness.sln, AdapterHarnessProject.btproj|Provides project, solution, and related files for the BizTalk project.|  
|mySchema.xsd|Provides the Instance.xml schema expected by the harness orchestration from the receive part of the adapter, as well as the schema of the Instance.xml handed to the send part of the adapter by the orchestration.|  

|\Design Time\Adapter Management files|Description|  
|---------------------------------------------|-----------------|  
|AdapterManagement.cs, AdapterManagement.csproj, AdapterManagement.sln|Project, solution, and related files for the adapter design-time.|  
|AssemblyInfo.cs|Contains assembly information for this sample.|  
|CategorySchema2.xml|Not used by the sample adapter.|  
|CategorySchema.xml|Contains the service organization tree for the static adapter.|  
|DotNetFileResource.resx|Contains resources.|  
|ReceiveHandler.xsd, ReceiveLocation.xsd|Contains receive side handler and endpoint custom property schemas|  
|service1.wsdl|Contains operation definitions for the adapter.|  
|TransmitHandler.xsd, TransmitLocation.xsd|Contains transmit side handler and endpoint custom property schemas|  

|                                                                                                                                                             \Runtime files                                                                                                                                                              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DotNetFile.csproj, DotNetFile.sln,<br /><br /> AssemblyInfo.cs,<br /><br /> DotNetFileExceptions.cs, DotNetFileProperties.cs, DotNetFileReceiver.cs, DotNetFileReceiverEndPoint.cs, DotNetFileTransmitter.cs,<br /><br /> DotNetFileTransmitterEndpoint.cs,<br /><br /> DotNetFileAsyncTransmitterBatch.cs,<br /><br /> BatchMessage.cs | Files for the run-time file-copy send and receive adapters. You can modify and save these files under a new name for custom components.<br /><br /> DotNetFile.csproj and DotNetFile.sln are the project and solution files.<br /><br /> AssemblyInfo.cs contains assembly information for this sample.<br /><br /> DotNetFileReceiver.cs reads the files from the receive locations and submits them to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].<br /><br /> DotNetFileExceptions.cs,implements code to handle exceptions during message processing<br /><br /> DotNetFileProperties.cs, contains common properties for both Receive and Send operations<br /><br /> BatchMessage.cs, implements batch messaging.<br /><br /> DotNetFileReceiverEndPoint.cs, is a class corresponding to a Receive Location/URI.  It handles polling the given folder for new messages<br /><br /> DotNetFileTransmitter.cs is a singleton class for DotNetFile send adapter. All the messages, going to various send ports of this adapter type go through this class<br /><br /> DotNetFileTransmitterEndpoint.cs,handles transmitting messages. |

|\SDK\Samples\AdaptersDevelopment\BaseAdapter\v1.0.2 files|Description|  
|--------------------------------------------------------------------|-----------------|  
|Adapter.cs, AdapterException.cs, AsyncTransmitter.cs, batch.cs, ConfigProperties.cs, ControlledTermination.cs, IManageEndpoints.cs, Receiver.cs, ReceiverEndpoint.cs|Provides classes that constitute the Base Adapter. You can use these to create your own adapters.|  

## How to Use This Sample  
 Use the sample file adapter as a template on which to create other custom adapters.  

## Building This Sample  

> [!IMPORTANT]
>  If the BizTalk installation is 64-bit or the location of installation is modified, OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath would need to be changed accordingly.  

 Use the following procedures to build and initialize the File Adapter sample.  

#### To create a strong name key for the DotNetFileAdapter projects and the Base Adapter project  

1.  Start **Visual Studio Command Prompt**.  

    > [!NOTE]
    >  Run the command prompt as an Administrator.  

2.  Change the current directory to the \<*Samples Path*\>**\AdaptersDevelopment\BaseAdapter\v1.0.2** directory.  

3.  At the command prompt, type **sn –k BaseAdapter.snk** and then press ENTER. This .snk file may already exist as a result of other samples being run previously. If so, you can go right to step 4 and skip this step.  

4.  Change the current directory to the \<*Samples Path*\>\\**AdaptersDevelopment\File Adapter\Runtime** directory.  

5.  At the command prompt, type **sn –k DotNetFileAdapter.snk** and then press ENTER.  

6.  At the command prompt, type **exit** and then press ENTER to close the command prompt window.  

#### To build the receiver run-time project  

1.  Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.  

2.  Navigate to the \<*Samples Path*\>**”\AdaptersDevelopment\File Adapter\Runtime”** directory, and then double-click **DotNetFile.sln**.  

3.  To rebuild the Adapter Receiver run-time project, in Solution Explorer, right-click **DotNetFile**, and then click **Rebuild**.  

4.  From the **File** menu, click **Exit** to close Visual Studio.  

#### To build the adapter design-time project  

1.  In Windows Explorer, navigate to the \<*Samples Path*\>**”\AdaptersDevelopment\File Adapter\Design Time\Adapter Management”** directory, and then double-click **AdapterManagement.sln**.  

2.  In Solution Explorer, right-click **AdapterManagement**, and then click **Rebuild**.  

3.  From the **File** menu, click **Exit** to close Visual Studio.  

#### To register the sample static adapter  

1. In Windows Explorer, navigate to the \<*Samples Path*\>**”\AdaptersDevelopment\File Adapter”** directory.  

2. To add the sample adapter to the registry, double-click **StaticAdapterManagement.reg**.  

   > [!NOTE]
   >  StaticAdapterManagement.reg includes hard-coded paths to C:\Program Files\Microsoft BizTalk Server\\. If you did not install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the %ProgramFiles%\Microsoft BizTalk Server\ directory, if you upgraded your BizTalk Server installation from BizTalk Server 2009 or BizTalk Server 2006 R2, or if you installed BizTalk Server on a computer that is running a 64-bit version of Windows, you must modify the file StaticAdapterManagement.reg with the appropriate paths. By default, BizTalk Server is installed into the %ProgramFiles(x86)%\Microsoft BizTalk Server\ directory on computers that are running a 64-bit version of Windows. Update the paths associated with the "InboundAssemblyPath", "OutboundAssemblyPath" and "AdapterMgmtAssemblyPath" values to point to the correct location of the specified files.  
   > 
   > [!IMPORTANT]
   >  If you install BizTalk on a 64 bit machine, change all instances of the HKEY_CLASSES_ROOT\CLSID\ registry entry to HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ in the **StaticAdapterManagement.reg** registry file.  

3. In the **Registry Editor** dialog box, click **Yes** to add the sample adapter to the registry, and then click **OK**.  

4. To close Windows Explorer, on the **File** menu, click **Close**.  

#### To install the sample static adapter  

1. Click **Start**, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then select **BizTalk Server Administration**.  

2. In the BizTalk Server Administration console, click to expand **BizTalk Server Administration**, click to expand **BizTalk Group**, and click to expand **Platform Settings**.  

3. Right click **Adapters**, click **New**, and then click **Adapter**.  

4. In the **Add Adapter** dialog box, do the following.  


   |  Use this   |                      To do this                       |
   |-------------|-------------------------------------------------------|
   |  **Name**   |                   Type **Static**.                    |
   | **Adapter** | Select **Static DotNetFile** from the drop-down list. |
   | **Comment** |               Type **Sample Adapter**.                |


5. Click **OK**.  

    The static adapter now appears in the list of adapters in the right window of the BizTalk Administration console.  

#### To stop and restart the host instance  

1. Click **Start**, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and select **BizTalk Server Administration**.  

2. In the BizTalk Server Administration console, click to expand **BizTalk Server Administration**, click to expand **BizTalk Group**, click to expand **Platform Settings** and click **Host Instances**. Select the BizTalkServerApplication in the right pane.  

3. In the results pane, right-click the host instance (typically, the computer name), and then click **Restart**.  

### Running This Sample  

##### To run the File Adapter sample  

1. Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.  

2. Create the following folders on the BizTalk Server installation drive:  

   -   *\<drive\>*:**\Temp**  

   -   *\<drive\>*:**\Temp\Send**  

   -   *\<drive\>*:**\Temp\Receive**  

3. To close Windows Explorer, on the **File** menu, click **Close**.  

4. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

5. Right-click the **BizTalk Server Administration**  node and select **Connect to Existing Group**.  

6. In the **Connect to Existing BizTalk Server Configuration Database** dialog box, do the following.  

   > [!NOTE]
   >  The BizTalk Management database is also referred to as the BizTalk Configuration database.  

   |    Use this    |                                                                                    To do this                                                                                     |
   |----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **SQL Server** |                                                                              Type **.** (a period).                                                                               |
   |  **Database**  | Select the name of the BizTalk Management database that was created by the Configuration Wizard. The default database name used by the Configuration Wizard is **BizTalkMgmtDb**. |


7. Click **OK**.  

8. Expand the **BizTalk Group[*server name*]** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand the **Applications** node, expand the  **BizTalk Application 1** node.  

9. Right-click the **Send Ports** node, and then click **New**, select **Static One-Way Send Port**, and then click **OK**.  

10. In the **Send Port Properties** dialog box, select **General**, and do the following.  


    |      Use this      |                                                                                                                                                                                   To do this                                                                                                                                                                                   |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |      **Name**      |                                                                                                                                                                             Type **AdapterSend**.                                                                                                                                                                              |
    | **Transport Type** | Select **Static** from the drop-down list and click **Configure**.<br /><br /> -   In the **Directory** box, type ***\<drive\>*:\Temp\Send**.<br />-   In the **File Mode** box, select **CreateNew**.<br />-   In the **File Name** box, type **%MessageID%.xml**.<br />-   Click **OK**.<br />-   The **URI** field should show ***\<drive\>*:\Temp\Send\\%MessageID%.xml**. |
    | **Send pipeline**  |                                                                                                                                   Select **PassThruTransmit (Microsoft.BizTalk.DefaultPipelines.PassThruTransmit)**, and then click **OK**.                                                                                                                                    |


11. Under the **BizTalk Application 1** node click **Receive Ports**, and select **New / One-Way Receive Port**.  

12. In the **Create New Receive Port** dialog box, in the **Specify the type of Receive Port** box, select **One-way Receive Port** from the drop-down list, and then click **OK**.  

13. In the **Receive Port Properties** dialog box, in the **Name** box, type **AdapterReceive**, and then click **OK**.  

14. Under the **BizTalk Application 1** node right click **Receive Locations**, and select **New / One-way Receive Location**.  

15. In the **Select a Receive Port** dialog, select **AdapterReceive** then click **OK**.  

16. In the **Receive Location Properties** dialog box, do the following.  


    |       Use this       |                                                                                                                                                                                               To do this                                                                                                                                                                                                |
    |----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |       **Name**       |                                                                                                                                                                                     Type **AdapterReceiveLocation**                                                                                                                                                                                     |
    |  **Transport Type**  |                                                                                                                                                  Select **Static** from the drop-down list and hit **Configure** to access these remaining properties.                                                                                                                                                  |
    |       **URI**        | -   Click the ellipsis button (**…**).<br />-   In the **Number Of Files In Batch** box, type **20**.<br />-   In the **Directory** box, type ***\<drive\>*:\Temp\Receive**.<br />-   Ensure the **File Mask** property is set to **\*.xml**.<br />-   In the **Polling Interval** box, type **5**, and click **OK**.<br />-   Ensure the **URI** label contains ***\<drive\>*:\Temp\Receive\\\*.xml**. |
    | **Receive Handler**  |                                                                                                                                                                      Select **BizTalkServerApplication** from the drop-down list.                                                                                                                                                                       |
    | **Receive Pipeline** |                                                                                                                                                                             Select **XMLReceive** from the drop-down list.                                                                                                                                                                              |


17. Click **OK**.  

     Proceed to *Building, Deploying, and Binding the Sample Adapter*.  

### Building, Deploying, and Binding the Sample Adapter  
 Before the adapter goes live, you must build the project, bind the orchestration with the ports, and enlist the adapter.  

##### To create a strong name key for the static adapter  

1.  Start **Visual Studio Command Prompt**.  

2.  At the command prompt, change the current directory to the \<*Samples Path*\>**\AdaptersDevelopment\File Adapter\BizTalk Project\Adapter Harness** directory.  

3.  At the command prompt, type **sn –k AdapterHarness.snk**, and then pressENTER.  

4.  Click **OK**.  

##### To build the Adapter Harness project  

-   In Solution Explorer, right-click **AdapterHarnessProject**, and then click **Rebuild**.  

##### To deploy the Adapter Harness project  

1.  In Solution Explorer, when the project has rebuilt, right-click **AdapterHarnessProject**, and then click **Deploy**.  

2.  In BizTalk Server Administration console, select the project you have deployed, and then click **Refresh**.  

##### To bind the orchestration with the ports  

1. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, under the appropriate [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, expand the **Orchestrations** node.  

2. Right-click **AdapterHarness.AdapterHarnessType**, and then click **Bind**.  

3. In the **Port Binding Properties - AdapterHarness.AdapterHarnessType- Binding Configurations** dialog box, do the following.  


   |          Use this          |                     To do this                     |
   |----------------------------|----------------------------------------------------|
   | **AdapterFileReceivePort** | Select **AdapterReceive** from the drop-down list. |
   |  **AdapterFileSendPort**   |  Select **AdapterSend** from the drop-down list.   |


4. In the left pane, click **Host**.  

5. In the **Host** box, select **BizTalkServerApplication** from the drop-down list, and then click **OK**.  

   Proceed to *Administering the Sample Adapter*.  

### Administering the Sample Adapter  
 You complete administration tasks for the sample adapter in the BizTalk Administration console.  

##### To administer the File Adapter sample  

1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the left pane, click to expand **Applications**, click to expand **BizTalk Application 1**, and click **Receive Locations**.  

3. Ensure the **AdapterReceive** status is **Enabled**.  

    If the status is not **Enabled**, right-click **AdapterReceive** in the right pane, and then click **Enable**.  

4. In the left pane, click **Orchestrations** and ensure that **AdapterHarness.AdapterHarnessType** is **Enlisted**. Right click **AdapterHarness.AdapterHarnessType**, and then click **Enlist** (if AdapterHarness.AdapterHarnessType is already enlisted, the **Enlist** menu option is unavailable).  

5. Right-click **AdapterHarness.AdapterHarnessType** and select **Start**. The status of this orchestration should change to **Running**.  

   Proceed to *Testing the Sample Adapter*.  

### Testing the Sample Adapter  
 After you deploy the sample adapter, you must stop and restart the host instance. It is critical that you test the sample adapter before you place it into production.  

##### To stop and restart the host instance  

1.  In the **BizTalk Server Administration** console, click to expand **BizTalk Server Administration**, click to expand **BizTalk Group**, click to expand **Platform Settings** and click **Host Instances**. Select the BizTalkServerApplication in the right pane.  

2.  Right-click the host instance (typically, the computer name), and then click **Stop**.  

     The status of the host instance changes to **Stopped**.  

3.  Right-click the host instance, and then click **Start**.  

     The status of the host instance changes to **Running**.  

##### To test the sample static adapter runtime  

1.  In Windows Explorer, navigate to the \<*Samples Path*\>**\AdaptersDevelopment\File Adapter** directory, and copy the InstanceXML.xml file to your clipboard.  

2.  Navigate to *\<drive\>*:**\Temp\Receive** and paste the Instance.xml file into the folder.  

     If the transmit and receive adapters are working, the file should move from the *\<drive\>*:**\Temp\Receive** folder to the *\<drive\>*:**\Temp\Send** folder.  

##### To test the sample Add Adapter Wizard functionality for the sample static adapter  

1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click **AdapterHarnessProject**, point to **Add**, and then click **Add Generated Items**.  

2. In the **Add Generated Items - AdapterHarnessProject** dialog box, click **Add Adapter Metadata**, and then click **Open**.  

    The list of registered adapters appears.  

3. Select **Static DotNetFile**, and then click **Next**.  

    The service organization exposed by the adapter appears.  

4. Expand **Service Organization**, **Health Care**, and then click **Administrative**.  

    Notice that **Eligibility** displays differently from the other nodes. **Eligibility** is a service node that you can select. The other nodes are organization nodes that do not describe any specific service.  

5. Select the **Eligibility** node, and then click **Finish**.  

    BizTalk imports an .odx file and an .xsd file into the project.  

    You can now use the schemas, PortTypes, Operations, and MessageTypes imported from the adapter in the schedule for the BizTalk project.  

## Classes or Methods used in this Sample  
 Interfaces: IBaseMessage, IPropertyBag, IBTTransportProxy  

 Classes (from Base Adapter): AsyncTransmitterEndpoint, AsyncTransmitter, BatchMessage, ControlledTermination, ReceiverEndpoint, DotNetFileCommonProperties, BatchOperationType  

### Comments  
 After completing the sample adapter, you can modify the sample adapter to create a custom static or dynamic adapter For more information, see [Adapter Design-Time Configuration](../core/adapter-design-time-configuration.md).  

## See Also  
 [Adapter Samples - Usage](../core/adapter-samples-usage.md)   
 [Registering an Adapter](../core/registering-an-adapter.md)