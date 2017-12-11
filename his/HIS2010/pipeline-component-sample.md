---
title: "Pipeline Component Sample | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c01e995-9ad2-4b6e-a7e8-97b168d4b7d0
caps.latest.revision: 3
---
# Pipeline Component Sample
The Pipeline component sample describes the three components necessary to put messages into an MQSeries queue with the MQRFH2 header: a pipeline component project, a pipeline project that makes use of the pipeline component, and a test application that puts messages into the queue.  
  
## Location in the SDK  
 \<Installation directory>\SDK\Samples\Adapters\MQSC\MQRFH2Sample  
  
## File Inventory  
 The following table shows the files in the sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|In the / BizTalkServerMQRFH2Pipeline folder|Describes the BizTalk pipeline project that contains both receive and send pipeline.|  
|In the / MQRFH2PipelineComponent folder|Contains the pipeline component that reads MQRFH2 properties from the MQSeries message and promotes it into BizTalk context properties in the receive scenario. Similarly, on the send side, the component can set these MQRFH2 properties in the MQSeries message based on values provided through the context properties..|  
|In the MQRFH2TestDriver folder|Contains an application that can send MQSeries messages to an MQSeries queue with the MQRFH2 header.|  
  
## How to Use the Sample  
 Use the following instructions to build, deploy, configure, and run the sample.  
  
#### To build and deploy the sample  
  
1.  Open MQRFH2TestDriver.cpp and specify the correct channelName, connectionName, qmgrName and qName to correct values that match what you have configured in your WebSphere MQ Server configuration.  
  
2.  Save the file.  
  
3.  Run \<InstallPath>\SDK\Samples\Adapters\MQSC\MQRFH2Sample\setup.bat to build the projects and deploy the pipeline component and pipeline project in BizTalk.  
  
#### To configure and run the sample  
  
1.  Create a BizTalk receive port and receive location using MQSC adapter to point to an MQ queue on a MQ Server (MQServer1\QM1\RECVQ).  
  
2.  Associate MQRFHReceivePipeline with this receive location.  
  
3.  Configure a send port using MQSC Adapter to point to an MQ queue on a MQ Server (MQServer1\QM2\SENDQ).  
  
4.  Create a subscription that uses the receive port created in step1.  
  
     This will enable a round trip receive-send scenario between MQ->BizTalk->MQ. Associate MQRFHSendPipeline with this send port.  
  
5.  Enable the receive location and start the send port.  
  
6.  Start the host instance associated with these end-points.  
  
7.  Use MQRFH2TestDriver.exe to put an MQSeries message to MQServer1\QM1\RECVQ.  
  
8.  Check the MQSeries queue MQServer1\QM2\SENDQ to see the new message that was sent from BizTalk Server.  
  
     You can view the message in MQSeries queue to see the MQRFH2 header.  
  
## See Also  
 [MQSC Adapter Samples](../HIS2010/mqsc-adapter-samples.md)