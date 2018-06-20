---
title: "Tutorial: Using the BizTalk Adapter for PeopleSoft Enterprise to Retrieve Data from PeopleSoft Enterprise | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c173fa4c-911e-4fa3-813f-e8f36b0049a5
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorial: Using the BizTalk Adapter for PeopleSoft Enterprise to Retrieve Data from PeopleSoft Enterprise
The BizTalk Adapter for PeopleSoft Enterprise can be used to execute a query against a PeopleSoft system and return the results of the query. This walkthrough describes an SDK sample that illustrates this functionality.  

## Prerequisites  

- The Java 2 Platform must be installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise Geis running on.  

- The PeopleSoft Java Object Adapter JAR file, **psjoa.jar** should be copied to a folder that is accessible to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on.  

- [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] must be installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on in order to build and deploy the sample.  

## What This Sample Does  
 This sample picks up an XML file from a folder, sends the file to an orchestration, and then uses the BizTalk Adapter for PeopleSoft Enterprise to execute a query against a PeopleSoft system. The result of the query is written to an XML file.  

## How This Sample is Designed and Why  
 This sample was designed in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and was created to illustrate basic functionality using the BizTalk Adapter for PeopleSoft Enterprise with a BizTalk orchestration.  

## Where to Find This Sample  
 The sample is located in the following folder:  

 \Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Sdk\PeopleSoftTwoWaySend  

 The following table shows the files in this sample and describes their purpose.  


|                               **Runtime Project Filename**                                |                                                                                                                                                                           **Runtime Project File Description**                                                                                                                                                                            |
|-------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                       TwoWaySend.btproj,<br /><br /> TwoWaySend.sln                       |                                                                                                                                                                      Project and solution files for the application.                                                                                                                                                                      |
| LOCATIONService.xsd,<br /><br /> LOCATIONService_1.xsd,<br /><br /> LOCATIONService_2.xsd | Schema files for the application. **Note:**  The adapter schema files in the project were originally created using the **Add Adapter Metadata Wizard**. For more information on the Add Adapter Metadata Wizard see the topic "How to Add Adapter Metadata to a BizTalk Project" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation. |
|                                 PeopleSoftTwoWaySend.odx                                  |                                                                                                                                                                        The orchestration used by the application.                                                                                                                                                                         |
|                                 PeopleSoftTwoWaySend.snk                                  |                                                                                                                                                                                The strong naming key file.                                                                                                                                                                                |

## How to Use This Sample  

#### Create a new instance of the PeopleSoft Enterprise adapter  

1. Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. Click **Start**, **Programs**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **BizTalk Server Administration**.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.  

3. Right-click **Adapters** and point to **New**, **Adapter** to display the **Adapter Properties** dialog.  

4. Enter a value for the **Name** field, for example **PeopleSoft**.  

5. Select **PeopleSoft Enterprise(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.  

#### Create a Solicit-Response BizTalk Send Port  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.  

2. Right-click **Send Ports** and point to **New**, **Static Solicit-Response Send Port** to display the **Send Port Properties** dialog.  

3. Enter a value for the **Name** field, for example **PeopleSoftTwoWaySP**.  

4. Select the PeopleSoft adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.  

   > [!NOTE]
   >  This value is the name that was specified when the PeopleSoft Enterprise adapter was created in the Administration Console.  

5. Enter the following values for the **Adapter Required Properties**:  


   |       **Property**       |                                                                                                                                        **Value**                                                                                                                                         |
   |--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | Application server path  | PeopleSoft Server's machine and port location, for example //PSServer:8888. **Note:**  If you do not specify a port number, the default port of 9000 is used so in the example above you could enter a value of //PSServer if the PeopleSoft Server uses the default port value of 9000. |
   |        JAVA_HOME         |                                                                                          Path to the home directory associated with the Java 2 Platform SDK files, for example C:\j2sdk1.4.2_08                                                                                          |
   |         Password         |                                                                                                                 Password used when connecting to the PeopleSoft system.                                                                                                                  |
   | PeopleSoft 8.x JAR files |                                                                                          Location of the PeopleSoft Java Object Adapter JAR file, **psjoa.jar**, for example C:\JARS\psjoa.jar.                                                                                          |
   |        User name         |                                                                                                                    Username for connecting to the PeopleSoft system.                                                                                                                     |


6. Click **OK**.  

7. Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown.  

8. Select the **XMLReceive** pipeline from the list of pipelines available in the **Receive pipeline** dropdown and click **OK**.  

9. Right-click the send port and click **Start** to enlist and start the send port.  

#### Create a One-Way BizTalk Send Port  

1. Create a target folder to be used by the send port, for example C:\Files\Out.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.  

3. Right-click **Send Ports** and point to **New**, **Static One-Way Send Port** to display the **Send Port Properties** dialog.  

4. Enter a value for the **Name** field, for example **PeopleSoftTwoWayFileSP**.  

5. Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.  

6. Enter the location of the folder that you created earlier for the **Destination Folder** property and click **OK**.  

7. Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.  

8. Right-click the send port and click **Start** to enlist and start the send port.  

#### Create a file receive port  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.  

2. Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port** to display the Receive Port Properties dialog.  

3. Enter a value for the **Name** field, for example **PeopleSoftTwoWayFileRP**, and click **OK**.  

#### Create a file receive location  

1.  Create a folder to be monitored by the file receive location, for example C:\Files\In.  

2.  Right-click the new receive port and then click **New**, **Receive Location** to display the **Receive Location Properties** dialog.  

3.  Enter a value for the **Name** field, for example **PeopleSoftTwoWayFileRL**.  

4.  Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.  

5.  Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.  

6.  Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.  

7.  Right-click the receive location and click **Enable**.  

#### Modify the Adapter schema target namespace property  

1. Launch [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and open TwoWaySend.sln. Click **File**, **Open**, **Project/Solution** to display the **Open Project** dialog.  

2. Browse to the TwoWaySend.sln file, click to select this file and click **Open** to open the solution that contains the sample project.  

3. Click the **View** menu and select **Solution Explorer** to display the Solution Explorer.  

4. Double-click the LOCATIONService_1.xsd file in the Solution Explorer to open it.  

5. Right-click the **Schema** node of LOCATIONService_1.xsd and select the **Properties** menu option to display the properties for the schema.  

6. Edit the **Target Namespace** property to use the appropriate values for the adapter name, for example the **Target Namespace** property should read as follows:  

   ```  
   http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]  
   ```  

    Where *PeopleSoft* is the name of the PeopleSoft adapter as viewed in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  

   > [!IMPORTANT]
   >  If the configured value for **Target Namespace** does not match the namespace specified in the input document instance then a routing failure will occur when the input document instance is processed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

#### Generate a document instance from the Adapter schema  

1.  Double-click **LOCATIONService_1.xsd** in Solution Explorer to open the file in Schema Editor.  

2.  Right-click the **\<Schema\>** node in Schema Editor and click **Properties** to display properties for the node.  

3.  Select **Get** from the list of available nodes in the **Root Reference** dropdown box. This should be done so that when you generate a sample document instance it will be generated from the **Get** node of the schema.  

4.  Right-click **LOCATIONService_1.xsd** in Solution Explorer and click **Properties** to display properties in the Properties window.  

5.  In the Properties window, click to select the **Output Instance Filename** option.  

6.  Click the ellipses button (…) to display the **Select Output File** dialog.  

7.  Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.  

    > [!NOTE]
    >  Do not specify the location of the folder that was specified for the file receive location here.  

8.  Right-click LOCATIONService_1.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.  

9. Right-click the **\<Schema\>** node in Schema Editor and click **Properties** to display the properties for the node.  

10. Select (**Default)** from the list of available nodes in the **Root Reference** dropdown box.  

#### Modify the generated document instance  

1.  Open the generated document instance in a text editor such as Notepad and edit the contents of the document instance to ensure that the data in these fields will return an existing record:  

    ```  
    <ns0:Get xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
    <ns0:SETID>SHARE</ns0:SETID>  
    <ns0:LOCATION>WFKLOC</ns0:LOCATION>  
    <ns0:getHistory>true</ns0:getHistory>  
    </ns0:Get>  
    ```  

    > [!NOTE]
    >  In the example above, *PeopleSoft* is a placeholder for the actual name of the adapter as viewed in the BizTalk Administration Console. *SHARE* and *WFKLOC* are placeholders for values used to identify a particular record in the PeopleSoft system.  

2.  Save the modified document instance.  

#### Build and deploy the project  

1. Right-click the TwoWaySend project in Solution Explorer and click **Properties** to display the Project Designer for the project.  

2. Click the **Deployment** tab in the Project Designer.  

3. Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group**.  

4. Right-click the TwoWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.  

#### Bind and Enlist the orchestration  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.  

2. Click the **Refresh** button in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console view.  

3. Double-click the orchestration to display the **Orchestration Properties** dialog.  

4. Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.  

5. Specify the appropriate values for the binding options, for example:  


   |      **Parameter**      |        **Value**         |
   |-------------------------|--------------------------|
   |          Host           | BizTalkServerApplication |
   |     FileReceivePort     |  PeopleSoftTwoWayFileRP  |
   | PeopleSoftTwoWaySend678 |    PeopleSoftTwoWaySP    |
   |      ResponsePort       |  PeopleSoftTwoWayFileSP  |


6. Click OK.  

#### Start the orchestration  

- In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the orchestration and click **Start** to enlist and start the orchestration.  

#### Drop a document instance into the folder monitored by the file receive location  

-   Copy the document instance that was created earlier to the folder that the file receive location is configured to monitor.  

#### Verify that the document instance was processed by the BizTalk Adapter for PeopleSoft Enterprise  

- Open the folder that the file send port is configured to send to and verify that an output document was generated. This file should contain the results of the query that was processed by the BizTalk Adapter for PeopleSoft Enterprise.  

  The following sequence of events occurs if the document instance is processed successfully:  

1.  The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.  

2.  The orchestration subscribes to this published message so the BizTalk Messaging Engine activates an instance of the orchestration and sends the message to the orchestration instance.  

3.  The orchestration instance publishes the message back to the MessageBox.  

4.  The solicit-response send port subscribes to this published message so the BizTalk Messaging Engine sends the message to the PeopleSoft send port.  

5.  The send port hands the message to the BizTalk Adapter for PeopleSoft Enterprise.  

6.  The BizTalk Adapter for PeopleSoft Enterprise executes a Get statement against the PeopleSoft system using the parameters defined in the input file.  

7.  The BizTalk Adapter for PeopleSoft Enterprise returns the results of the Get statement as the response message for the solicit-response port in the orchestration.  

8.  The orchestration publishes the result set to the MessageBox.  

9. The File send port subscribes to this message so BizTalk sends the message to the File adapter.  

10. The File adapter writes the message containing the result set to the designated output folder.  

## See Also  
 [Tutorials: Using BizTalk Adapter for PeopleSoft Enterprise](../core/tutorials-using-biztalk-adapter-for-peoplesoft-enterprise.md)