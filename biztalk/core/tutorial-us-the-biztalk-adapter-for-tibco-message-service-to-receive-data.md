---
title: "Tutorial: Using the BizTalk Adapter for TIBCO Enterprise Message Service to Receive Data | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc5a63ec-1897-4c9b-b37f-cdcec151b1c9
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorial: Using the BizTalk Adapter for TIBCO Enterprise Message Service to Receive Data
You can use the BizTalk Adapter for TIBCO Enterprise Message Service (EMS) to receive data from a TIBCO system. This walkthrough describes an SDK sample that illustrates this.  

## Prerequisites  

- BizTalk Adapter for TIBCO Enterprise Message Service requires that you add the TIBCO EMS C# API, TIBCO.EMS.dll, to the global assembly cache (GAC). For more information about installing the assembly, see [TIBCO Enterprise Message Service Requirements and Limitations](../core/tibco-enterprise-message-service-requirements-and-limitations.md).  

- Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.  

## What This Sample Does  
 This sample picks up an XML file from a folder, sends the file to an orchestration, and then uses the BizTalk Adapter for TIBCO Enterprise Message Service to retrieve data from a TIBCO system. The result is written to an XML file.  

## How This Sample is Designed and Why  
 This sample, designed in Visual Studio, illustrates basic functionality using the BizTalk Adapter for TIBCO Enterprise Message Service with a BizTalk orchestration.  

> [!NOTE]
>  The sample assumes that you know how to send a message from TIBCO for the application to process.  

## Where to Find This Sample  
 The default location for the sample is  

 C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Enterprise Message Service(TM)\Sdk\OneWayReceive  

 The following table shows the files in this sample and describes their purpose.  

|**Runtime Project Filename**|**Runtime Project File Description**|  
|----------------------------------|------------------------------------------|  
|OneWayReceive.btproj,<br /><br /> OneWayReceive.sln|Project and solution files for the application.|  
|Schema.xsd,|Schema file for the application.|  
|Orchestration.odx|The orchestration used by the application.|  
|TIBCOEMSOneWaySend.snk|The strong naming key file.|  

## How to Use This Sample  

#### Create a new instance of the BizTalk Adapter for TIBCO EMS  

1. Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. Click **Start**, **Programs**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **BizTalk Server Administration**.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.  

3. Right-click **Adapters** and point to **New**, **Adapter** to display the **Adapter Properties** dialog.  

4. Enter a value for the **Name** field, for example **TIBCO EMS**.  

5. Select **TIBCO Enterprise Message System** from the list of adapters available in the **Adapter** dropdown and click **OK**.  

#### Create a BizTalk Receive Port  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.  

2. Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port** to display the Receive Port Properties dialog.  

3. Enter a value for the **Name** field, for example **TIBCOEMSOneWayRP**, and click **OK**.  

#### Create a BizTalk Receive Location  

1. Right-click the new receive port and then click **New**, **Receive Location** to display the **Receive Location Properties** dialog.  

2. Enter a value for the **Name** field, for example **TIBCOEMSOneWayRL**.  

3. Select the TIBCO EMS adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.  

   > [!NOTE]
   >  This value is the name that was specified when the TIBCO adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  

4. Enter values for the **Server Connection definition**:  


   | **Property** |                                **Value**                                |
   |--------------|-------------------------------------------------------------------------|
   | Destination  |               The server destination queue or topic name.               |
   | Port number  | The port on which the TIBCO server is listening. Default value is 7222. |
   | Server Name  |                    The name of the TIBCO EMS server.                    |


5. Enter values for the **User Credentials**:  

   |**Property**|**Value**|  
   |------------------|---------------|  
   |Password|The password for the TIBCO EMS server.|  
   |User name|The user name for the TIBCO EMS server.|  

    For more information about the properties, see [Creating TIBCO Enterprise Message Service Receive Handlers](../core/creating-tibco-enterprise-message-service-receive-handlers.md).  

6. Click **OK**.  

7. Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.  

8. Right-click the receive location and click **Enable**.  

#### Create a one-way file send port  

1. Create a target folder to be used by the send port, for example C:\FilesOut.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.  

3. Right-click **Send Ports** and point to **New**, **Static One-way Send Port** to display the **Send Port Properties** dialog.  

4. Enter a value for the **Name** field, for example **TIBCOEMSOneWayFileSP**.  

5. Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.  

6. For the **Destination Folder** property, enter the location of the folder that you created earlier and click **OK**.  

7. Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.  

8. Right-click the send port and click **Start** to enlist and start the send port.  

#### Build and deploy the project  

1. Right-click the OneWayReceive project in Solution Explorer and click **Properties** to launch the Project Designer for the project.  

2. Click the **Deployment** tab.  

3. Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group** category.  

4. Right-click the OneWayReceive project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.  

#### Bind and Enlist the orchestration  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.  

2. Click the **Refresh** button in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.  

3. Double-click the orchestration to display the **Orchestration Properties** dialog.  

4. Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.  

5. Specify the appropriate values for the binding options, for example:  


   |         **Parameter**          |        **Value**         |
   |--------------------------------|--------------------------|
   |              Host              | BizTalkServerApplication |
   |          FileSendPort          |   TIBCOEMSOneWayFileSP   |
   | TibcoEMSOneWayReceiveOperation |     TIBCOEMSOneWayRP     |


6. Click **OK**.  

#### Start the orchestration  

- In the [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] Administration console, right-click the orchestration and click **Start** to enlist and start the orchestration.  

#### Verify that the application receives a message  

- Open the folder that the file send port is configured to send to and verify that an output document was generated. This file should contain the results of the query that was processed by the BizTalk Adapter for TIBCO Enterprise Message Service.  

  The following sequence of events occurs if the document instance is processed successfully:  

1.  The TIBCO EMS adapter receives a message from TIBCO system and publishes it to the MessageBox as a BizTalk message.  

2.  The orchestration subscribes to this published message so the BizTalk Messaging Engine activates an instance of the orchestration and sends the message to the orchestration instance.  

3.  The orchestration instance publishes the message back to the MessageBox.  

4.  The File send port subscribes to this message so BizTalk sends the message to the File adapter.  

5.  The File adapter writes the message containing the result set to the designated output folder.  

## See Also  
 [Tutorial: Using the BizTalk Adapter for TIBCO Enterprise Message Service to Send Data](../core/tutorial-use-tibco-enterprise-message-service-adapter-in-biztalk-to-send-data.md)   
 [Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Enterprise Message Service](../core/tutorials-use-the-microsoft-biztalk-adapter-for-tibco-message-service.md)   
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)