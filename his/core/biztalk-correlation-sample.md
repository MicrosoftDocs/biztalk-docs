---
title: "BizTalk Correlation Sample | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e616630b-38ca-4d62-8b87-e63b6c0d1a2c
caps.latest.revision: 4
---
# BizTalk Correlation Sample
The BizTalk Correlation sample describes how to retrieve messages from an MQSeries queue and put the response messages into another MQSeries queue.  
  
## Location in the SDK  
 \<Installation directory>\SDK\Samples\Adapters\MQSC\MQSSolicitResponse  
  
## File Inventory  
 The following table shows the files in the sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|In the /MQSCorrelationSetOrchestrationWithSolicitResponse folder|The BizTalk Orchestration project that contains associations between file and MQSeries end-points along with the correlation sets.|  
|In the / MQSSolicitResponseApp folder|The application that retrieves messages from an MQSeries queue and puts a response message to another MQSeries queue.|  
  
## How to Use the Sample  
 Use the following procedures to build, deploy, configure, and run the sample.  
  
#### To build and deploy the sample  
  
1.  On your BizTalk Server computer, open the orchestration project MQSCorrelationSetOrchestrationWithSolicitResponse\MQSCorrelationSolicitResponse.sln.  
  
2.  Open the orchestration MQSCorrelationSolicitResponse.odx.  
  
3.  Double-click on the message assignment shape MessageAssignment_1.  
  
4.  Adjust the assignment statements for the MQMD_ReplyToQ and MQMD_ReplyToQMgr context properties to point to MQServer1\QM1\QUEUEB.  
  
5.  Save the changes to this orchestration.  
  
6.  Run MQSCorrelationSetOrchestrationWithSolicitResponse\Setup.bat to build and deploy the orchestration to BizTalk.  
  
7.  Run MQSSolicitResponseApp\Setup.bat to build the test application.  
  
#### To configure and run the sample  
  
1.  Create a solicit-response send port, point it at MQServer1\QM1\QUEUEA  
  
2.  Create a receive port and a receive location, point it at MQServer1\QM1\QUEUEB  
  
3.  Bind the orchestration you deployed earlier to the solicit-response send port and receive port.  
  
4.  Create three folders: c:\temp\pickup2, c:\temp\moveit, and c:\temp\dropit2  
  
5.  Start the receive locations, send ports and the orchestration.  
  
6.  Put an XML file in the pickup2 folder.  
  
     For example, \<test>This is a test\</test>.  
  
7.  Observe the file disappear as it is picked up by BizTalk.  
  
8.  Observe the message arrive in MQServer1\QM1\QUEUEA.  
  
9. Observe the MQSeries response message arrive in c:\temp\moveit.  
  
     This message will be an XML file describing the message ID and correlation ID the MQSeries server assigned to the message.  
  
10. Observe that there is one active orchestration instance in the BizTalk Administration Console.  
  
     This is the long-running orchestration waiting for a message to correlate with the message that it already received.  
  
11. Use the test application MQSSolicitResponseApp to read the message BizTalk sent and send a response message.  
  
     You may also use the command line parameters to receive the message from MQServer1\QM1\QUEUEA.  
  
12. Observe a message arrive in c:\temp\dropit2.  
  
     This message is the response message from the test application.  
  
## See Also  
 [MQSC Adapter Samples](../core/mqsc-adapter-samples.md)