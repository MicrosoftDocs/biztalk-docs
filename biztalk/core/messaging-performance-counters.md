---
description: "Learn more about: Messaging Performance Counters"
title: "Messaging Performance Counters"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Messaging Performance Counters
Performance counters allow you to monitor specific aspects of work performed on the site or system by service. Performance counters can help you identify and troubleshoot server performance issues.  
  
 The following performance counters are accessible for each host instance under the **BizTalk:Messaging** and the **BizTalk:Messaging Latency** performance object categories:  
  
|**Category**|**Counter**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:Messaging|Active receive locations|Number of receive locations currently enabled in this host instance.|  
||Active receive threads|Number of threads in the Messaging Engine currently processing messages received from adapters running in this host instance. These include messages that have been processed asynchronously by send adapters.|  
||Active send messages|Number of messages the Messaging Engine has currently in send processing. This includes messages currently in send pipeline processing as well as response messages for receive adapters.|  
||Active send threads|Number of threads in the Messaging Engine currently processing messages to send to adapters. This includes response messages to receive adapters.|  
||Documents processed|Documents processed.|  
||Documents processed/Sec|Documents processed/Sec.|  
||Documents received|Documents received.|  
||Documents received/Sec|Documents received per second.|  
||Documents resubmitted|Total number of documents resubmitted by send adapters.|  
||Documents submitted/Batch|Average number of documents submitted per batch.|  
||Documents suspended|Documents suspended.|  
||Documents suspended/Sec|Documents suspended per second.|  
||Documents transmitted/Batch|Average number of messages transmitted per batch.|  
||ID Process|The process identifier for this host instance.|  
||Pending receive batches|Number of batches received by the Messaging Engine that have not completed processing. These include batches that have been processed asynchronously by send adapters.|  
||Pending transmitted messages|Number of messages given by the Messaging Engine to send adapters that have not completed processing. This includes response messages for receive adapters.|  
||Request/Response timeouts|Number of request messages that have not received a response message within the time limit specified by the adapter.|  
||Throttled receive batches|Number of batches that have been blocked on receive by the Messaging Engine due to high service load. These batches contain new messages to be processed.|  
|BizTalk:Messaging Latency|Inbound Latency (sec)|Average latency in milliseconds from when the Messaging Engine receives a document from the adapter until the time it is published to Message Box.|  
||Outbound Adapter Latency (sec)|Average latency in milliseconds from when the adapter gets a document from the Messaging Engine until the time it is sent by the adapter.|  
||Outbound Latency (sec)|Average latency in milliseconds from when the Messaging Engine receives a document from the Message Box until the time document is sent by the adapter.|  
||Request-Response Latency (sec)|Average latency in milliseconds from when the Messaging Engine receives a request document from the adapter until the time a response document is given back to the adapter.|  
  
## To access performance counters  
 Use the following steps to access the performance counters.  
  
#### If you are using Windows 2008  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.  
  
2.  In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.  
  
3.  In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:Messaging** performance counter object and select the counters to be monitored  
  
4.  In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.  To select all available counter instances, select \<**All instances**\>.  
  
5.  After adding the counters, click **OK**.  
  
     The selected performance counters appear on the **Performance Monitor** screen.  
  
## See Also  
 [Performance Tips and Tricks](../core/performance-tips-and-tricks.md)   
 [Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Optimizing Resource Usage Through Host Throttling](../core/optimizing-resource-usage-through-host-throttling.md)
