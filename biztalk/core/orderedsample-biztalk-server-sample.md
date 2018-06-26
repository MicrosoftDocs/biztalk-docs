---
title: "OrderedSample (BizTalk Server Sample) | Microsoft Docs"
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
  - "MQSeries adapters, examples"
ms.assetid: 7e59ff43-d425-40cd-9725-af13084f83d9
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# OrderedSample (BizTalk Server Sample)
The OrderedSample sample demonstrates how to use an orchestration to receive and send an ordered series of messages in a round-trip fashion.  
  
## What This Sample Does  
 The sample assumes there are messages in the MQSeries queue from which it receives messages. When the adapter reads the messages from MQSeries queue, it reads them in-order and submits them to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 The receive port in the orchestration, **mqreceive**, has its **Ordered Delivery** property set to **True**.  
  
 For the send side, the orchestration sends a message and then waits for a delivery notification before sending the next message. The send port, **mqsend** has its **Delivery Notification** property set to **Transmitted**. To keep the example simple, the orchestration uses an infinite loop.  
  
 The orchestration can receive batches of messages and single messages.  
  
## Where to Find This Sample  
 *\<Samples Path\>*\AdaptersUsage\MQSeriesAdapter\OrderedSample  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File|Description|  
|----------|-----------------|  
|OrderedReceiveSend.btproj,<br /><br /> OrderedReceiveSend.sln|Project and solution files for the application.|  
|OrderedReceiveSendOrchestration.odx|The orchestration of the application.|  
|OrderedSample.snk|The strong naming key file.|  
|**Setup.bat**|Builds and initializes this sample.|  
  
## Building and Running the Sample  
  
#### To build and deploy the sample  
  
1. In a command window, navigate to the following folder:  
  
    `<Samples Path>\AdaptersUsage\MQSeriesAdapter\OrderedSample`  
  
2. Run the file Setup.bat, which performs the following actions:  
  
   1.  Creates a strong name key for the project.  
  
   2.  Compiles and deploys the orchestration project.  
  
   If you have the required permissions to the MQSeries Server for Windows installation, you can create the MQSeries queue through the adapter dialog boxes, and can skip the next procedure. If you do not have such access, you can create the queue using the IBM WebSphere MQ Explorer. To create the queues through the WebSphere MQ Explorer, complete the following steps.  
  
## Creating the MQSeries Queues Through the WebSphere MQ Explorer  
  
#### To create the MQSeries queues through the WebSphere MQ Explorer  
  
1.  Click **Start**, point to **All Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.  
  
2.  Double-click **Queue Managers**, and then double-click the **default queue manager**. The default queue manager is typically named QM_<machine_name> where machine_name is the name of your computer.  
  
3.  Right-click **Queues**, point to **New**, and then click **Local Queue**.  
  
4.  In **Create Local Queue** dialog box, in **Queue Name**, type **"queue1"**, and then click **OK**.  
  
5.  Right-click **Queues**, click **New**, and then click **Local Queue**.  
  
6.  In the **Create Local Queue** dialog box, in **Queue Name**, type **"queue2"**, and then click **OK**.  
  
## Creating the Receive Location and the MQSeries Queue  
 This procedure creates the send port and receive location to send the message to and receive the correlation message from MQSeries. The MQSeries queue will also be created when you create the receive location if not already created.  
  
#### To create the receive location and the MQSeries queue  
  
1.  Open the BizTalk Server Administration console.  
  
2.  Expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the required application.  
  
3.  Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  
  
4.  In the **One-way Receive Port Properties** dialog box type, in the **Name** box type **OrderedSampleReceive** and click **OK**.  
  
5.  In the left pane, click **Receive Locations** tab, and then click **New**.  
  
6.  In the **Receive Location Properties** dialog box, in the **Name** box type "**OrderedSampleReceiveLocation**".  
  
7.  In the **Transport Type** box, select **MQSeries**.  
  
8.  In the **Receive Handler** box, select **BizTalkServerApplication**.  
  
9. In the **Receive pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.  
  
10. Click **Configure**.  
  
11. In the **MQSeries Transport Properties** dialog box, in the **Polling Interval** box, type **"10"**.  
  
12. In the **Queue Definition** box, click the **ellipsis (…)** button.  
  
13. In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.  
  
14. In the **Queue Manager** box, select the **default queue manager**.  
  
15. In the **Queue** box, type " **queue1**", and then click **Export**.  
  
16. In the **Export** dialog box, click **Create Queue**, and then click **OK** or **Done** until you have exited all dialog boxes.  
  
## Creating the Send Port and MQSeries Queue  
  
#### To create the send port and MQSeries queue  
  
1.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
2.  In the **Static Port Properties** dialog box type, in the **Name** box, type "**OrderedSampleSend**".  
  
3.  In the **Transport Type** box, select **MQSeries**.  
  
4.  In the **Send pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.  
  
5.  Click **Configure**.  
  
6.  In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** box, click the **ellipsis (…)** button.  
  
7.  In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.  
  
8.  In the **Queue Manager** box, select the **default queue manager**.  
  
9. In the **Queue** box, type " **queue2**", and then click **Export**.  
  
10. In the **Export** dialog box, click **Create Queue**, and then click **OK** or **Done** until you have exited all dialog boxes.  
  
#### To enable the receive location and start the send port  
  
1.  In the BizTalk Server Administration console, click **Receive Ports**.  
  
2.  In the details pane, right-click the **MQIn** receive location and click **Enable**.  
  
3.  In the details pane, right-click the **MQOut** send port and click **Start.**  
  
#### To bind and start the Orchestration  
  
1.  In the BizTalk Server Administration console, expand the **Orchestrations** folder.  
  
2.  Double-click the **OrderedSampleOrchestration** orchestration, and then click  **Bindings**.  
  
3.  Bind the orchestration ports to the following send ports and receive locations:  
  
    |Orchestration Port|Messaging Port / Receive Location|  
    |------------------------|----------------------------------------|  
    |mqreceive|OrderedSampleReceive|  
    |mqsend|OrderedSampleSend|  
  
4.  Click **Host**.  
  
5.  In the **Host** box, select **BizTalkServerApplication**, and click **OK**.  
  
6.  Right click the **Orchestration** and click **Start**.  
  
#### To run the sample  
  
1.  Start the orchestration.  
  
2.  Put messages into the MQSeries queue from which you have configured the receive location to read.  
  
3.  View the messages in WebSphere MQ Explorer in the send queue to which you have configured the send port to send messages.  
  
## See Also  
 [MQSeries Adapter Samples](../core/mqseries-adapter-samples.md)