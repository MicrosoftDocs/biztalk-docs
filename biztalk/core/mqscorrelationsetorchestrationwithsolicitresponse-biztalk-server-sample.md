---
title: "MQSCorrelationSetOrchestrationWithSolicitResponse (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "examples, MQSeries adapters"
  - "orchestrations, examples"
  - "examples, orchestrations"
  - "examples, messages"
  - "messages, examples"
  - "MQSeries adapters, examples"
ms.assetid: 5127d743-bb79-4e97-a2f3-446892e1bfa0
caps.latest.revision: 29
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MQSCorrelationSetOrchestrationWithSolicitResponse (BizTalk Server Sample)
The MQSCorrelationSetOrchestrationWithSolicitResponse sample demonstrates how to use a correlation identifier produced by the MQSeries Server instead of by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## What This Sample Does  
 The orchestration sends a message with an empty value for the **MQMD_MsgID** property in the message header. MQSeries generates the MessageID and CorrelationID and returns a message with a value assigned to **MQMD_MsgID** and **MQMD_CorrelId** as part of the response in the solicit-response send port of the adapter. The orchestration uses the generated correlation identifier to initialize the correlation set and follows the correlation set in a subsequent receive location by checking the **MQMD_CorrelId** property of the message. The adapter also assigns the correlation identifier to **BizTalk_CorrelationID**, which you could also use in an orchestration. For more information about using correlation identifiers with the adapter, see [Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md).  
  
> [!IMPORTANT]
>  Orchestrations using this technique may experience problems if the message from the MQSeries Server arrives before the correlation identifier. Make sure that you design your orchestrations to allow enough time for the MQSeries Server to return the correlation identifier. This example does not consider this possible race condition.  
  
## Where to Find This Sample  
 *\<Samples Path\>*\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestrationWithSolicitResponse  
  
 The following table shows the files in this sample and describes their purpose.  
  
|**File**|**Description**|  
|--------------|---------------------|  
|**MQSCorrelationSolicitResponse.btproj,**<br /><br /> **MQSCorrelationSolicitResponse.sln**|Project and solution files for the application.|  
|**MQSCorrelationSolicitResponse.odx**|The BizTalk orchestration file for the application.|  
|**MQSCorrelationSolicitResponse.snk**|The strong naming key file.|  
|Setup.bat|Builds and initializes this sample.|  
  
## How to Use This Sample  
 To create the application, you must complete the following steps:  
  
- Create two MQSeries queues.  
  
- Set up a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location and send port.  
  
- Enable the receive location.  
  
- Start the send port.  
  
- Create the appropriate folders.  
  
- Modify the orchestration.  
  
- Deploy, bind and start the orchestration.  
  
  If you have the required permissions to the MQSeries Server for Windows installation, you can create the MQSeries queue through the adapter dialog boxes, and can skip the next procedure. If you do not have such access, you can create the queue using the IBM WebSphere MQ Explorer. To create the queues through the WebSphere MQ Explorer, complete the following steps.  
  
## Creating the MQSeries Queues Through the WebSphere MQ Explorer  
  
#### To create the MQSeries queues through the WebSphere MQ Explorer  
  
1.  Click **Start**, point to **All Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.  
  
2.  Double-click **Queue Managers**, and then double-click the default queue manager. The default queue manager is typically named **QM_***<machine_name>* where *machine_name* is the name of your computer.  
  
3.  Right-click **Queues**, point to **New**, and then click **Local Queue**.  
  
4.  In **Create Local Queue** dialog box, in **Queue Name**, type "REPLYTOQ", and then click **OK**.  
  
5.  Right-click **Queues**, click **New**, and then click **Local Queue**.  
  
6.  In the **Create Local Queue** dialog box, in **Queue Name**, type "SOLICITRESPONSEQ", and then click **OK**.  
  
## Creating the Receive Location and the MQSeries Queue  
 This procedure creates the send port and receive location to send the message to and receive the correlation message from MQSeries. The MQSeries queue will also be created when you create the receive location if not already created.  
  
#### To create the receive location and the MQSeries queue  
  
1.  Open the BizTalk Server Administration console.  
  
2.  Expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the required application.  
  
3.  Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  
  
4.  In the **One-way Receive Port Properties** dialog box, in the **Name** box, type "MQReply", and click **OK**.  
  
5.  In the left pane, click **Receive Locations** tab, and then click **New**.  
  
6.  In the **Receive Location Properties** dialog box, in the **Name** box, type "MQReply”.  
  
7.  In the **Transport Type** box, select **MQSeries**.  
  
8.  In the **Receive Handler** box, select **BizTalkServerApplication**.  
  
9. In the **Receive pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.  
  
10. Click **Configure**.  
  
11. In the **MQSeries Transport Properties** dialog box, in the **Polling Interval** box, type "10".  
  
12. In the **Queue Definition** box, click the ellipsis (…) button.  
  
13. In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.  
  
14. In the **Queue Manager** box, select the default queue manager.  
  
15. In the **Queue** box, type " REPLYTOQ", and then click **Export**.  
  
16. In the **Export** dialog box, click **Create Queue**, and then click**OK**or **Done** until you have exited all dialog boxes.  
  
## Creating the Send Port and MQSeries Queue  
  
#### To create the send port and MQSeries queue  
  
1.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
2.  In the **Send Port Properties** dialog box, in the **Name** box, type "MQSolicitResponse".  
  
3.  In the **Transport Type** box, select **MQSeries**.  
  
4.  In the **Send pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.  
  
5.  In the **Receive pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.  
  
6.  Click **Configure**.  
  
7.  In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** box, click the ellipsis (…) button.  
  
8.  In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.  
  
9. In the **Queue Manager** box, select the default queue manager.  
  
10. In the **Queue** box, type " SOLICITRESPONSEQ", and then click **Export**.  
  
11. In the Export dialog box, click **Create Queue**, and then click **OK** or **Done** until you have exited all dialog boxes.  
  
## Enabling the Receive Location and Starting the Send Port  
 This procedure creates the folders required to receive the file into the orchestration and sends the correlated message and response message to the output folders.  
  
#### To enable the receive location and start the send port  
  
1.  In the BizTalk Server Administration console, click **Receive Ports**.  
  
2.  In the details pane, right-click the **MQIn** receive location and click **Enable**.  
  
3.  In the details pane, right-click the **MQOut** send port and click **Start.**  
  
## Creating the Folders Used by the Application  
  
#### To create the folders used by the application  
  
1.  If one does not already exist, create a folder named "temp" on your C:\ drive.  
  
2.  Create folders under the **C:\temp** directory named "Pickup2", "Dropit2", and "MoveIt".  
  
## Modifying the Orchestration Used by the Application  
 This procedure modifies the orchestration used by the application.  
  
||  
|-|  
|To modify the Orchestration used by the application|  
|- In Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], double-click the solution file, **MQSCorrelationSolicitResponse.sln**, to open the solution.<br /><br /> - From the Solution Explorer pane, double-click the orchestration **MQSCorrelationSolicitResponse.odx** to view the orchestration.<br /><br /> - Double-click the message assignment shape **MessageAssignment_1** to launch the BizTalk Expression Editor.<br /><br /> - Enter the appropriate MQSeries queue manager name for the following expression:<br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_ReplyToQMgr) = "QM_<machine_name>";`<br /><br /> - If you would like for the response message sent from BizTalk to contain the entire contents of the original message instead of only the first 100 bytes, modify the following line in the BizTalk Expression Editor.<br /><br /> - Original line:<br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_Report) = 768;`<br /><br /> Change to:<br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_Report) = 1792;`<br /><br /> - In the BizTalk Expression Editor, click **OK** to save the modified expression.<br /><br /> - In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], select **File**, and then select **Save All**.|  
  
## Building and Deploying the Sample  
 This procedure builds and deploys the solution that contains the orchestration used in this application.  
  
#### To build and deploy the sample  
  
1.  In a command window, navigate to the following folder:  
  
     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestrationWithSolicitResponse`  
  
2.  Run the file Setup.bat, which performs the following actions:  
  
    1.  Creates a strong name key for the project.  
  
    2.  Compiles and deploys the orchestration project.  
  
    3.  Creates a send port and a receive port with the File adapter.  
  
    > [!NOTE]
    >  Since this orchestration specifies the bindings for sending and receiving files with the file adapter, when you deploy the orchestration the necessary send ports, receive port, and receive location will be created for receiving a file into the orchestration and outputting the correlation message and the response message.  
  
## Binding and Starting the Orchestration  
 This procedure binds the orchestration to the host and appropriate send ports and receive locations.  
  
#### To bind and start the orchestration  
  
1.  In the BizTalk Server Administration console, expand the **Orchestrations** folder.  
  
2.  In the details pane, right-click the **MQSCorrelationSolicitResponse** orchestration and click **Bind**.  
  
3.  Bind the orchestration ports to the following send ports and receive locations:  
  
    |**Orchestration Port**|**Messaging Port / Receive Location**|  
    |----------------------------|--------------------------------------------|  
    |FileReceivePort|MQSCorrelationSolicitResponse.Orchestration.FileReceivePort|  
    |MQSeriesResponseReceivePort|MQReply|  
    |SolicitResponsePort|MQSolicitResponse|  
    |TempPort|MQSCorrelationSolicitResponse.Orchestration.TempPort|  
    |FileSendPort|MQSCorrelationSolicitResponse.Orchestration.FileSendPort|  
  
4.  Click **Host**.  
  
5.  In the **Host** box, select **BizTalkServerApplication** and click **OK**.  
  
6.  In **Send Ports**, right-click **MQSCorrelationSolicitResponse.Orchestration.TempPort**, and then select **Start**.  
  
7.  In **Send Ports**, right-click **MQSCorrelationSolicitResponse.Orchestration.FileSendPort**, and then select **Start**.  
  
8.  In **Receive Locations**, right-click **MQSCorrelationSolicitResponse.Orchestration.FileReceivePort**, and then select **Enable**.  
  
9. Right-click the orchestration and click **Start**.  
  
    > [!NOTE]
    >  Starting the orchestration also automatically enlists the orchestration.  
  
## Testing the Application  
 This procedure tests the application.  
  
#### To test the application  
  
1. Put a file in the **C:\Temp\Pickup2** folder.  
  
2. Examine the files in the **C:\Temp\Dropit2** folder and the **C:\Temp\Moveit**folder.  
  
   - The **C:\Temp\Dropit2** folder should contain a copy of the message that was originally picked up by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
   - The **C:\Temp\Moveit**folder should contain a response document with the message identifier (MQMD_MsgId) and the correlation identifier (MQMD_CorrelId).  
  
   > [!NOTE]
   >  If you disable the **MQReply** receive location, you can examine the message in WebSphere MQ Explorer and see that the message and correlation identifiers are set. To do this, launch the **WebSphere MQ Explorer** and examine the message placed in the **REPLYTOQ** queue. The message and correlation identifiers are displayed on the **Identifiers** tab of the **Messageproperties** dialog box.  
  
## See Also  
 [Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md)   
 [MQSeries Adapter Samples](../core/mqseries-adapter-samples.md)