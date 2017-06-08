---
title: "HTTP Adapter Performance Counters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d85473f1-1d67-4990-8d2f-fc7fe0e80108
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Adapter Performance Counters
Performance counters allow you to monitor specific aspects of work performed on the site or system by service. Performance counters can help you identify and troubleshoot server performance issues.  
  
 The following performance counters are accessible for each host instance under the **BizTalk:HTTP Receive Adapter** and the **BizTalk:HTTP Send Adapter** performance object categories:  
  
|**Category**|**Counter**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:HTTP Receive Adapter|Memory queue size|Number of incoming messages in the HTTP receive adapter's internal memory queue.|  
||Message received|Total number of HTTP requests received by the HTTP receive adapter. The counter is incremented after a request message is completely read by the HTTP receive adapter from the HTTP client.|  
||Messages received/Sec|Number of HTTP requests received by the HTTP receive adapter per second. The counter applies only to request messages that have been completely read by the HTTP receive adapter from the HTTP client.|  
||Messages sent|Total number of HTTP responses sent by the HTTP receive adapter. The counter is incremented only for response messages that have been successfully sent to HTTP clients.|  
||Messages sent/Sec|Number of HTTP responses sent by the HTTP receive adapter per second. The counter applies only to response messages that have been successfully sent to HTTP clients.|  
||Time to add message to batch|Average time between when a message is given to the HTTP receive adapter by IIS and when the message is added to a batch.|  
||Time to build batch|Average time taken by the HTTP receive adapter to build a message batch.|  
|BizTalk:HTTP Send Adapter|Memory queue size|Number of outgoing messages in the HTTP send adapter's internal memory queue.|  
||Messages received|Total number of HTTP response messages received by the HTTP send adapter. The counter is incremented after a response message is completely read by the HTTP send adapter from HTTP servers.|  
||Message received/Sec|Number of HTTP responses received by the HTTP send adapter per second. The counter applies only to response messages that have been completely read by the HTTP send adapter from HTTP servers.|  
||Messages sent|Total number of HTTP requests sent by the HTTP send adapter. The counter is incremented only for request messages that have reached the destination URL.|  
||Messages sent/Sec|Number of HTTP requests sent by the HTTP send adapter per second. The counter applies only to request messages that have reached the destination URL.|  
  
## To access performance counters  
 Use the following steps to access the performance counters.  
  
#### If you are using Windows 2008  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.  
  
2.  In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.  
  
3.  In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:HTTP** performance counter object and select the counters to be monitored  
  
4.  In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.  To select all available counter instances, select \<**All instances**>.  
  
5.  After adding the counters, click **OK**.  
  
     The selected performance counters appear on the **Performance Monitor** screen.  
  
## See Also  
 [Monitoring BizTalk Server](../core/monitoring-biztalk-server.md)   
 [HTTP Adapter Configuration and Tuning Parameters](../core/http-adapter-configuration-and-tuning-parameters.md)   
 [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)