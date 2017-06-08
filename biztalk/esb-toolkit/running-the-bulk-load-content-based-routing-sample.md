---
title: "Running the Bulk Load Content-Based Routing Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e981567-7c6c-4c13-bd5b-597efdd3fb50
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running the Bulk Load Content-Based Routing Sample
This part of the sample demonstrates bulk loading a queue with messages that the ESB and Microsoft BizTalk will route to different destination queues based on the queue name specified in each message. It uses the features of the sample that you have seen in the previous two parts.  
  
 **To run the Bulk Load Content-based Routing Access sample**  
  
1.  If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.  
  
2.  Run the IBM RfhUtil utility, and then select the queue manager named ESB.JMS.Sample.QueueManager in the first drop-down list to connect to this queue manager, as in Part 2 of this sample.  
  
3.  In the second drop-down list, select the target outbound queue named ESB.JMS.SAMPLE.SENDTOBIZTALK, as in Part 2 of this sample.  
  
4.  Click the **Load Q** button in the RfhUtil utility, and then navigate to the test message file named TEST-000128.JMS located in the subfolder named \Source\Samples\JMS\Test\Data\Load\\. This file contains a batch of 128 test messages that the sample will send to the ESB.  
  
5.  In the **Load** dialog box, leave all values set to their default values.  
  
6.  In the **Load** dialog box, click **OK** to add all the messages to the input queue.  
  
7.  After a delay while the application executes, the ESB output messages appear in various destination queues, depending on the values in their JMS headers. However, all specify the same Reply To queue, so all the replies appear in the ESB.JMS.SAMPLE.REPLY queue. Open the WebSphere Queue Explorer and browse the queues to confirm this.