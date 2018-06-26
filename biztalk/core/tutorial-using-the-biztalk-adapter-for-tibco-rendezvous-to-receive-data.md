---
title: "Tutorial: Use the TIBCO Rendezvous adapter to receive | Microsoft Docs"
description: Step-by-step guide to use BizTalk Adapter for TIBCO Rendezvous in BizTalk Server to receive data from the TIBCO system
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58e7a739-701d-4085-a840-54f81c55e943
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Receive Data
You can use the BizTalk Adapter for TIBCO Rendezvous to receive data from a TIBCO system. This walkthrough describes an SDK sample that illustrates this.  

## Prerequisites  

Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.  

## About the sample 
- This sample uses the BizTalk Adapter for TIBCO Rendezvous to receive data from a TIBCO system. An orchestration processes the message and, using the file adapter, writes the data as an XML file in a specified folder.  

- This sample, designed in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], illustrates basic functionality using the BizTalk Adapter for TIBCO Enterprise Message Service with a BizTalk orchestration.  

    > [!NOTE]
    >  The sample assumes that you know how to send a message from TIBCO for the application to process.  

- The default location for the sample is `C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWayReceive`, and includes the following files: 

    |**Runtime Project Filename**|**Runtime Project File Description**|  
    |---|---|  
    |OneWayReceive.btproj,<br /><br /> OneWayReceive.sln|Project and solution files for the application.|  
    |PureMessage.xsd,|Schema file for the application.|  
    |TIBCORvOWR.odx|The orchestration used by the application.|  
    |TIBCORv.snk|The strong naming key file.|  


## Step 1: Add the adapter to BizTalk Administration

1.  In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.  

3.  Right-click **Adapters** and point to **New**, **Adapter…** to display the **Adapter Properties** dialog.  

4.  Enter a value for the **Name** field, for example **TIBCO Rendezvous**.  

5.  Select **TIBCO(r) Rendezvous(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.  

## Step 2: Create a Receive Port  

1.  In  **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.  

2.  Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port...** to display the **Receive Port Properties** dialog.  

3.  Enter a value for the **Name** field, for example **TIBCORvOneWayRP**, and click **OK**.  

## Step 3: Create a Receive Location  

1. Right-click the new receive port and then click **New**, **Receive Location…** to display the **Receive Location Properties** dialog.  

2. Enter a value for the **Name** field. For example, enter **TIBCORvOneWayRL**.  

3. Select the TIBCO Rendezvous adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.  

   > [!NOTE]
   >  This value is the name that was specified when the TIBCO adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  

4. Enter a value for the **RendezvousSubjectName** under the **AdapterRequiredProperties**.  

5. Enter values for the **Certified Listener Properties**:  


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

    For more information about the properties, see [Create Receive artifacts](../core/creating-tibco-rendezvous-receive-handlers.md).  

8. Click **OK**.  

9. Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.  

10. Right-click the receive location and click **Enable**.  

## Step 4: Create a one-way send port  

1. Create a target folder to be used by the send port, for example C:\FilesOut.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.  

3. Right-click **Send Ports** and point to **New**, **Static One-Way Send Port…** to display the **Send Port Properties** dialog.  

4. Enter a value for the **Name** field, for example **TIBCORvOneWayFileSP**.  

5. Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.  

6. For the **Destination Folder** property, enter the location of the folder that you created earlier and click **OK**.  

7. Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.  

8. Right-click the send port and click **Start** to enlist and start the send port.  

## Step 5: Build and deploy the project  

1. Right-click the OneWayReceive project in Solution Explorer and click **Properties** to launch the Project Designer for the project.  

2. Click the **Deployment** tab.  

3. Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group** category.  

4. Right-click the OneWayReceive project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.  

## Step 6: Bind, Enlist, and start the orchestration  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.  

2. Click the **Refresh** button in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.  

3. Double-click the orchestration to display the **Orchestration Properties** dialog.  

4. Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.  

5. Specify the appropriate values for the binding options, for example:  


   | **Parameter** |        **Value**         |
   |---------------|--------------------------|
   |     Host      | BizTalkServerApplication |
   |   SendPort    |   TIBCORvOneWayFileSP    |
   |  ReceivePort  |     TIBCORvOneWayRP      |


6. Click **OK**.  

7. Right-click the orchestration, and click **Start** to enlist and start the orchestration.  

## Step 7: Confirm the application receives a message  

- Open the folder that the file send port is configured to send to, and verify that an output document was generated.  

  The following sequence of events occurs if the document instance is processed successfully:  

1.  The TIBCO Rendezvous adapter receives a message from TIBCO system and publishes it to the MessageBox as a BizTalk message.  

2.  The orchestration subscribes to this published message so the BizTalk Messaging Engine activates an instance of the orchestration and sends the message to the orchestration instance.  

3.  The orchestration instance publishes the message back to the MessageBox.  

4.  The File send port subscribes to this message so BizTalk sends the message to the File adapter.  

5.  The File adapter writes the message containing the result set to the designated output folder.  

## See Also  
 [Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Send Data](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data.md)   
 [Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md)   
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)