---
title: "Tutorial: Using the BizTalk Adapter for PeopleSoft Enterprise to Write Data to PeopleSoft Enterprise | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 837dd4db-576d-41c1-9fe8-e1e46861270b
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorial: Using the BizTalk Adapter for PeopleSoft Enterprise to Write Data to PeopleSoft Enterprise
The BizTalk Adapter for PeopleSoft Enterprise can be used to write data to a PeopleSoft System with information received from a trading partner or internal application. This walkthrough describes an SDK sample that illustrates this functionality.  

## Prerequisites  

- The Java 2 Platform must be installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on.  

- The PeopleSoft Java Object Adapter JAR file, **psjoa.jar** should be copied to a folder that is accessible to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on.  

- [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] must be installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on in order to build and deploy the sample.  

## What This Sample Does  
 This sample picks up an XML file from a folder, sends the file to an orchestration, and then uses the BizTalk Adapter for PeopleSoft Enterprise to create a record in the PeopleSoft system from the data in the XML file.  

## How This Sample is Designed and Why  
 This sample was designed in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and was created to illustrate basic functionality using the BizTalk Adapter for PeopleSoft Enterprise with a BizTalk orchestration.  

## Where to Find This Sample  
 The sample is located in the following folder:  

 \Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Sdk\PeopleSoftOneWaySend  

 The following table shows the files in this sample and describes their purpose.  


|                               **Runtime Project Filename**                                |                                                                                                                                                                           **Runtime Project File Description**                                                                                                                                                                            |
|-------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                       OneWaySend.btproj,<br /><br /> OneWaySend.sln                       |                                                                                                                                                                      Project and solution files for the application.                                                                                                                                                                      |
| LOCATIONService.xsd,<br /><br /> LOCATIONService_1.xsd,<br /><br /> LOCATIONService_2.xsd | Schema files for the application. **Note:**  The adapter schema files in the project were originally created using the **Add Adapter Metadata Wizard**. For more information on the Add Adapter Metadata Wizard see the topic "How to Add Adapter Metadata to a BizTalk Project" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation. |
|                                 PeopleSoftOneWaySend.odx                                  |                                                                                                                                                                        The orchestration used by the application.                                                                                                                                                                         |
|                                 PeopleSoftOneWaySend.snk                                  |                                                                                                                                                                                The strong naming key file.                                                                                                                                                                                |

## How to Use This Sample  

#### Create a new instance of the PeopleSoft Enterprise adapter  

1. Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. Click **Start**, **All Programs**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], **BizTalk Server Administration**.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.  

3. Right-click **Adapters** and point to **New**, **Adapter…** to display the **Adapter Properties** dialog.  

4. Enter a value for the **Name** field, for example **PeopleSoft**.  

5. Select **PeopleSoft Enterprise(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.  

#### Create a BizTalk Send Port  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.  

2. Right-click **Send Ports** and point to **New**, **Static One-Way Send Port** to display the **Send Port Properties** dialog.  

3. Enter a value for the **Name** field, for example **PeopleSoftOneWaySP**.  

4. Select the PeopleSoft adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.  

   > [!NOTE]
   >  This value is the name that was specified when the PeopleSoft Enterprise adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  

5. Enter the following values for the **Adapter Required Properties**:  


   |       **Property**       |                                                                                                                                        **Value**                                                                                                                                         |
   |--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | Application server path  | PeopleSoft Server's machine and port location, for example //PSServer:8888. **Note:**  If you do not specify a port number, the default port of 9000 is used so in the example above you could enter a value of //PSServer if the PeopleSoft Server uses the default port value of 9000. |
   |        JAVA_HOME         |                                                                                          Path to the home directory associated with the Java 2 Platform SDK files, for example C:\j2sdk1.4.2_08                                                                                          |
   |         Password         |                                                                                                                 Password used when connecting to the PeopleSoft system.                                                                                                                  |
   | PeopleSoft 8.x JAR files |                                                                                          Location of the PeopleSoft Java Object Adapter JAR file, **psjoa.jar**, for example C:\JARS\psjoa.jar.                                                                                          |
   |        User name         |                                                                                                                    Username for connecting to the PeopleSoft system.                                                                                                                     |


6. Click **OK**.  

7. Select the **XML Transmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.  

8. Right-click the send port and click **Start** to enlist and start the send port.  

#### Create a file receive port  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.  

2. Right-click the Receive Ports folder and then click **New**, **One-way Receive Port** to display the Receive Port Properties dialog.  

3. Enter a value for the **Name** field, for example **PeopleSoftOneWayFileRP**, and click **OK**.  

#### Create a file receive location  

1.  Create a folder to be monitored by the file receive location, for example C:\Filesource.  

2.  Right-click the new receive port and then click **New**, **Receive Location** to display the **Receive Location Properties** dialog.  

3.  Enter a value for the **Name** field, for example **PeopleSoftOneWayFileRL**.  

4.  Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.  

5.  Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.  

6.  Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.  

7.  Right-click the receive location and click **Enable**.  

#### Modify the Adapter schema target namespace property  

1. Launch [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and open OneWaySend.sln. Click **File**, **Open**, **Project/Solution…** to display the **Open Project** dialog.  

2. Browse to the OneWaySend.sln file, click to select this file and click **Open** to open the solution that contains the sample project.  

3. Click the **View** menu and select **Solution Explorer** to display the Solution Explorer.  

4. Double-click the LOCATIONService_1.xsd file in the Solution Explorer to open it.  

5. Right-click the **Schema** node of LOCATIONService_1.xsd and select the **Properties** menu option to display the properties for the schema.  

6. Edit the **Target Namespace** property to use the appropriate values for the adapter name, for example the **Target Namespace** property should read as follows:  

   ```  
   http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]  
   ```  

    Where *PeopleSoft* is the name of the PeopleSoft adapter as viewed in the BizTalk Administration Console.  

   > [!IMPORTANT]
   >  If the configured value for **Target Namespace** does not match the namespace specified in the input document instance then a routing failure will occur when the input document instance is processed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

#### Generate a document instance from the Adapter schema  

1.  Double-click **LOCATIONService_1.xsd** in the Solution Explorer to open the file in the Schema Editor.  

2.  Right-click the **\<Schema\>** node in the Schema Editor, and click **Properties** to display the properties for the node.  

3.  Select **CreateEx** from the list of available nodes in the **Root Reference** dropdown box. This should be done so that when you generate a sample document instance it will be generated from the **CreateEx** node of the schema.  

4.  Right-click LOCATIONService_1.xsd in Solution Explorer and click **Properties**.  

5.  In the Properties window, click to select the **Output Instance Filename** option under the **General** section.  

6.  Click the ellipses button (…) to display the **Select Output File** dialog.  

7.  Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.  

    > [!NOTE]
    >  Do not specify the location of the folder that was specified for the file receive location here.  

8.  Right-click LOCATIONService_1.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.  

9. Right-click the **\<Schema\>** node in the Schema Editor, and click **Properties** to display the properties for the node.  

10. Select (**Default)** from the list of available nodes in the **Root Reference** dropdown box.  

#### Modify the generated document instance  

1.  Open the generated document instance in a text editor such as Notepad and edit the contents of the document instance to ensure that the data in these fields will generate a unique record in the PeopleSoft system, for example the XML file below describes the fields in a record that define a location:  

    ```  
    <ns0:CreateEx xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
      <ns0:SETID>SHARE</ns0:SETID>  
      <ns0:LOCATION>9991</ns0:LOCATION>  
      <ns0:interactiveMode>true</ns0:interactiveMode>  
       <ns0:properties>  
        <ns0:LOCATION_TBL_sequence>  
          <ns0:LOCATION_TBL>  
            <ns0:COUNTRY>USA</ns0:COUNTRY>  
            <ns0:DESCR>Adapter Test</ns0:DESCR>  
            <ns0:EFFDT>2006-05-31</ns0:EFFDT>  
            <ns0:EFF_STATUS>A</ns0:EFF_STATUS>  
            <ns0:SETID>SHARE</ns0:SETID>  
          </ns0:LOCATION_TBL>  
        </ns0:LOCATION_TBL_sequence>  
      </ns0:properties>  
    </ns0:CreateEx>  
    ```  

    > [!NOTE]
    >  In the example above, *PeopleSoft* is a placeholder for the actual name of the adapter as viewed in the BizTalk Administration Console.  

2.  Save the modified document instance.  

#### Build and deploy the project  

1. Right-click the OneWaySend project in Solution Explorer and click **Properties** to launch the Project Designer.  

2. Click the **Deployment** tab.  

3. Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group**.  

4. Right-click the OneWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.  

#### Bind and Enlist the orchestration  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.  

2. Click the **Refresh** button in the MMC toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console view.  

3. Double-click the orchestration to display the **Orchestration Properties** dialog.  

4. Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.  

5. Specify the appropriate values for the binding options, for example:  


   |      **Parameter**       |        **Value**         |
   |--------------------------|--------------------------|
   |           Host           | BizTalkServerApplication |
   |     FileReceivePort      |  PeopleSoftOneWayFileRP  |
   | PeopleSoftOneWaySendPort |    PeopleSoftOneWaySP    |


6. Click OK.  

#### Start the orchestration  

- In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the orchestration and click **Start** to enlist and start the orchestration.  

#### Drop a document instance into the folder monitored by the file receive location  

-   Copy the document instance that was created earlier to the folder that the file receive location is configured to monitor.  

#### Verify that the PeopleSoft system is updated  

- Use the PeopleSoft web interface to verify that the record was created from the data in the XML file.  

  The following sequence of events occurs if the document instance is processed successfully:  

1.  The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.  

2.  The orchestration subscribes to this published message so the BizTalk Messaging Engine will activate an instance of the orchestration and send the message to the orchestration instance.  

3.  The orchestration instance processes the message using the logic specified in the orchestration and publishes the message back to the MessageBox.  

4.  The PeopleSoft send port subscribes to this published message and so the BizTalk Messaging Engine sends the message to the PeopleSoft send port.  

5.  The send port hands the message to the BizTalk Adapter for PeopleSoft Enterprise.  

6.  The BizTalk Adapter for PeopleSoft Enterprise invokes the CreateEx method to create a record using the data in the XML file.  

## See Also  
 [Tutorials: Using BizTalk Adapter for PeopleSoft Enterprise](../core/tutorials-using-biztalk-adapter-for-peoplesoft-enterprise.md)