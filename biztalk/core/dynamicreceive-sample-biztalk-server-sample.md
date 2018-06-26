---
title: "DynamicReceive Sample (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fa7c934-7ec3-45ad-b226-c8c53934ecb1
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# DynamicReceive Sample (BizTalk Server Sample)
The DynamicReceive sample demonstrates how to receive [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] messages from an MQSeries queue when the URI for the MQSeries queue is specified dynamically.  
  
## What This Sample Does  
 This sample dynamically creates an MQSeries queue as specified by the **queueManager**, **queue**, and **server** variables. It enables a dynamic receive scenario and obtains [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] messages from the dynamically specified MQSeries queue based on the filter criteria specified in the **MQMD_MsgId** and **MQMD_CorrelId** message properties.  
  
## How This Sample Was Designed and Why  
 The MQSeries adapter can dynamically receive messages from an MQSeries queue by specifying the URI address of the queue in the orchestration. This functionality is achieved by using a solicit-response send port in the orchestration.  
  
 To dynamically receive messages, specify the following in an **Expression** shape in the orchestration:  
  
1. Enable dynamic receive by setting the following property on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message: **MQSeries.DynamicReceive** = `'Yes'`  
  
2. Specify the address from which to get the messages by setting the port URI. Optionally you can specify the following:  
  
   -   Specify the wait interval before getting the messages by using the **MQSeries.WaitInterval** property on the message.  
  
   -   Specify match criteria for receiving messages. The match criteria options are **Message ID**, **CorrelationID**, **GroupID**, and **MessageSequenceNumber**. See "Properties Related to BizTalk Server" at [http://go.microsoft.com/fwlink/?LinkId=89396](http://go.microsoft.com/fwlink/?LinkId=89396) for more details.  
  
   After the message is created with these properties it is sent to the MQSeries queue by using a solicit-response send port. The port specifies the adapter to receive messages from the specified URI with the indicated match options. The following actions result:  
  
- If the filter criteria to obtain a message are satisfied, then the message is retrieved from the queue and is sent back to the orchestration.  
  
- If the filter criteria to obtain a message are not satisfied, a dummy response is returned. This is an indication that the specified options did not return any messages from the queue.  
  
  Using the dynamic receive functionality gives you additional flexibility because a fixed receive location is not required. In some cases, you may not know the URI until run time. Dynamic receive functionality allows you to dynamically determine from where to obtain messages. It also means you do not need to implement a queuing contract within an orchestration.  You can wait to obtain messages by using a dynamically specified URI from the MQSeries queue based on the specified match criteria.  
  
## Where to Find This Sample  
 \<*Samples Path*\>\Samples\AdaptersUsage\MQSeriesAdapter\DynamicReceive  
  
 The following table shows the files in this sample and describes their purpose.  
  
|||  
|-|-|  
|File|Description|  
|DynamicReceive.btproj,<br /><br /> DynamicReceive.sln|Project and solution files for the application.|  
|DynamicReceive e.odx|The BizTalk orchestration file for the application.|  
|Setup.bat|Batch file to create the key file, compile the project, and deploy it.|  
  
## How to Use This Sample  
 Specify the **Microsoft.XLANGs.BaseTypes.Address** that makes sense for your solution. Change the **MQSeries.WaitInterval** to specify when you expect to receive the response messages. Update (or add) the match options, or remove them if you plan to obtain all messages.  
  
## Building and Running the Sample  
  
#### To create the sample  
  
1. Create a new orchestration project in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2. Enable the dynamic receive operation by setting the **MQSeries.DynamicReceive** property on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message to `'Yes'`.  
  
3. Specify the address from which to obtain the messages by setting the **Port URI**.  
  
4. Optionally the following two properties can be specified:  
  
   1.  Specify a wait interval before getting the messages by using the **MQSeries.WaitInterval** property on the message.  
  
   2.  Specify match criteria for receiving messages. See "Match options" help for more details.  
  
5. Change the following variables in the orchestration to specify where to get the messages from:  
  
   -   **Queue**, **queueManager**, and **server**. These are used to build the URI in the **Expression** shape.  
  
6. Modify the **Expression** shape to comment out dynamic queue creation and match options as necessary.  
  
7. You can build and deploy the project in either of the following ways:  
  
   -   Open the solution, right click the project in Solution explorer and click **Properties** to view project properties. On the Signing tab click **\<New...\>** in the **Choose a strong name key file** drop down box. Then provide a key file name and deploy.  
  
   -   Alternatively, run the setup.bat file which creates the key file, builds the project and deploys it.  
  
#### To run the sample  
  
1.  Bind the orchestration to the BizTalk Host.  
  
2.  Enable the file receive port created by the orchestration. Change the file receive location from **c:\temp\in** to the proper file folder.  
  
3.  Enlist and start the two send ports that were created. One port is a dynamic solicit-response port type, while the other is a file send port and is the queue where the message will be sent. Ensure that this is set to the correct location.  
  
4.  To start the orchestration, drop a file in the input folder. This invokes the MQSeries adapter and calls the **MQSAgent2** COM+ component on the specified server to obtain the message. The received message appears in the folder location specified in the file send port.  
  
5.  If no message is found that matches the criteria specified in the **Expression** shape, a dummy message is dropped into the output folder. To disable match options, comment out the last two lines in the **Expression** shape.  
  
## Comments  
  
-   If the queue is being dynamically created, but not deleted, it will result in errors when the next orchestration instance is activated.  
  
-   There are other ways to set the URI dynamically; this sample specifies just one option. For example, the URI could be set by reading some property in the message context.  
  
-   If there are no messages in the queue that satisfy the match options, a dummy message is returned.  
  
-   Because this sample uses dynamic send ports, other options may need to be specified, such as retry and transactions. Use the context properties exposed by the adapter to set these options before sending the message out to the dynamic solicit-response port.  
  
-   MQSeries queues can be created and deleted dynamically by using the **MQSAdapterAdmin2** interface. For an example of how to dynamically create MQSeries queues, see "Support for Queue Management" at [http://go.microsoft.com/fwlink/?LinkId=89400](http://go.microsoft.com/fwlink/?LinkId=89400).