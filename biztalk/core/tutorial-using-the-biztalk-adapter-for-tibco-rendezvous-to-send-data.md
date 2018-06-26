---
title: "Tutorial: Use the TIBCO Rendezvous adapter to send | Microsoft Docs"
description: Step-by-step guide to use BizTalk Adapter for TIBCO Rendezvous in BizTalk Server to send data to the TIBCO system
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b761ce2d-3465-43e0-bd8d-4d68b523226a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Send Data
You can use the BizTalk Adapter for TIBCO Rendezvous to send data to a TIBCO system. This walkthrough describes an SDK sample that illustrates this.  

## Prerequisites  

- Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.  

- The sample uses a DLL containing message context properties: Microsoft.BizTalk.Adapters.TibRV.Properties.dll. You may need to update the solution's reference to this library. For more information, see [BizTalk Server Message Context Properties (Send Handlers)](../core/biztalk-server-message-context-properties-send-handlers.md).  

## About the sample 

- This sample picks up an XML file from a file folder, sends the file to an orchestration, and then uses the BizTalk Adapter for TIBCO Rendezvous to create a record in the TIBCO system.  

- This sample, designed in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], illustrates basic functionality using the BizTalk Adapter for TIBCO Rendezvous with a BizTalk orchestration.  

- The default location for the sample is `C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWaySend`, and includes the following files: 

    |**Runtime Project Filename**|**Runtime Project File Description**|  
    |---|---|  
    |OneWaySend.btproj<br /><br /> OneWaySend.sln|Project and solution files for the application.|  
    |Schema.xsd<br /><br /> PropertySchema.xsd|Schema and property schema files for the application.|  
    |Orchestration.odx|The orchestration used by the application.|  
    |TIBCORendezvousOneWaySend.snk|The strong naming key file.|  

## Step 1: Add the adapter to BizTalk Administration

1.  In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.  

3.  Right-click **Adapters** and point to **New**, **Adapter…** to display the **Adapter Properties** dialog.  

4.  Enter a value for the **Name** field. For example, enter **TIBCO Rendezvous**.  

5.  Select **TIBCO(r) Rendezvous(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.  

## Step 2: Create a Send Port  

1. In  **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.  

2. Right-click **Send Ports** and point to **New**, **Static One-Way Send Port…** to display the **Send Port Properties** dialog.  

3. Enter a value for the **Name** field, for example **TIBCORndOneWaySP**.  

4. Select the TIBCO Rendezvous adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.  

   > [!NOTE]
   >  This value is the name that was specified when the TIBCO Enterprise Message System adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  

5. Enter values for the **Certified Sender Properties**:  


   |   **Property**   |                                                                         **Value**                                                                          |
   |------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | Ledger file name |                                             Ledger file name to use for persistent certified message delivery.                                             |
   |  Reusable name   | Reusable correspondent name to use for certified message delivery. The name must be unique among all certified message correspondent names on the network. |


6. Enter values for the **Credentials**:  


   | **Property** |                   **Value**                    |
   |--------------|------------------------------------------------|
   |   Password   | The password for the TIBCO Rendezvous server.  |
   |  User name   | The user name for the TIBCO Rendezvous server. |


7. Enter values for the **RendezvousTransport**:  

   |**Property**|**Value**|  
   |------------------|---------------|  
   |Daemon|Rendezvous Transport Daemon parameter.|  
   |Network|Rendezvous Transport Network parameter.|  
   |Service|Rendezvous Transport Service parameter.|  

    For more information about the properties, see [Create the send artifacts](../core/creating-tibco-rendezvous-send-handlers.md).  

8. Click **OK**.  

9. Select the **XML Transmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.  

10. Right-click the send port and click **Start** to enlist and start the send port.  

## Step 3: Create a receive port  

1.  In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.  

2.  Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port...** to display the Receive Port Properties dialog.  

3.  Enter a value for the **Name** field, for example **TIBCORndOneWayFileRP**, and click **OK**.  

## Step 4: Create a receive location  

1.  Create a folder for the file receive location to monitor, for example C:\Filesource.  

2.  Right-click the new receive port and then click **New**, **Receive Location…** to display the **Receive Location Properties** dialog.  

3.  Enter a value for the **Name** field, for example **TIBCORndOneWayFileRL**.  

4.  Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.  

5.  Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.  

6.  Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.  

7.  Right-click the receive location and click **Enable**.  

## Step 5: Generate a document instance from the schema  

1.  In Visual Studio,right-click Schema.xsd in Solution Explorer, and click **Properties**.  

2.  In the Properties window, click to select the **Output Instance Filename** option under the **General** section.  

3.  Click the ellipses button (…) to display the **Select Output File** dialog.  

4.  Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.  

    > [!NOTE]
    >  Do not specify the location of the folder that was specified for the file receive location here.  

5.  Right-click Schema.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.  

## Step 6: Update the generated document instance  

1.  Open the generated document instance in a text editor(Notepad works), and edit the contents of the document instance to ensure that the data will generate a unique record in the TIBCO system. For example, the follow code shows the first part of the data file:  

    ```  
    <ns0:Root xmlns:ns0="http://TibcoRendezvousOneWaySend.TibcoRendezvousOneWaySendSchema">  
        <Name>Punya Palit</Name>  
        <MailAddress>Prose Ware, Inc.</MailAddress>  
    </ns0:Root>  
    ```  

2.  Save the modified document instance.  

## Step 7: Build and deploy the project  

1. Right-click the **OneWaySend** project in Solution Explorer and click **Properties** to launch the Project Designer for the project.  

2. Click the **Deployment** tab.  

3. Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group**.  

4. Right-click the OneWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.  

## Step 8: Bind, enlist, and start the orchestration  

1. In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.  

2. Click the **Refresh** button in the MMC toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.  

3. Double-click the orchestration to display the **Orchestration Properties** dialog.  

4. Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.  

5. Specify the appropriate values for the binding options, for example:  


   |    **Parameter**    |        **Value**         |
   |---------------------|--------------------------|
   |        Host         | BizTalkServerApplication |
   |   FileReceivePort   |   TIBCORndOneWayFileRP   |
   | TibcoRendezvousSend |     TIBCORndOneWaySP     |


6. Click OK.  

7. Right-click the orchestration, and click **Start** to enlist and start the orchestration.  

## Step 9: Drop a document, and check the TIBCO system

-   Copy the document instance that was created earlier to the file receive folder the application monitors.  

-   Use the TIBCO web interface to verify that the record was created from the data in the XML file.  


The following sequence of events occurs if the document instance is processed successfully:  

1.  The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.  

2.  The orchestration subscribes to this published message so the BizTalk Messaging Engine will activate an instance of the orchestration and send the message to the orchestration instance.  

3.  The orchestration instance processes the message using the logic specified in the orchestration and publishes the message back to the MessageBox.  

4.  The TIBCO send port subscribes to this published message and so the BizTalk Messaging Engine sends the message to the TIBCO send port.  

5.  The send port hands the message to the BizTalk Adapter for TIBCO Rendezvous.  

6.  The BizTalk Adapter for TIBCO Rendezvous sends the message to the TIBCO system.  

## See Also  
 [Tutorial: Use the BizTalk Adapter for TIBCO Rendezvous to Receive Data](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data.md)   
 [Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md)   
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)