---
title: "File Adapter Performance Counters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 343465b4-6b20-4a24-b4b1-138548c572cc
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File Adapter Performance Counters
Performance counters allow you to monitor specific aspects of work performed on the site or system by service. Performance counters can help you identify and troubleshoot server performance issues.  
  
 The following performance counters are accessible for each host instance under the **BizTalk:FILE Receive Adapter** and the **BizTalk:FILE Send Adapter** performance object categories:  
  
|**Category**|**Counter**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:FILE Receive Adapter|Bytes received|Total number of bytes received by the file receive adapter. The counter is incremented after a message is completely read by the adapter from the file system.|  
||Byte received/Sec|Number of bytes received by the file receive adapter per second. The counter applies only to messages that have been completely read by the file adapter from the file system.|  
||Delete retries|Number of times the file receive adapter attempts to delete a file that has been read.|  
||Lock failures|Number of times the file receive adapter failed to lock the file.|  
||Lock failures/sec|Number of times the file receive adapter failed to lock the file per second.|  
||Messages received|Total number of messages received by the file receive adapter. The counter is incremented after a message is completely read by the file receive adapter from the file system.|  
||Messages received/Sec|Number of messages received by the file receive adapter per second. The counter applies only to messages that have been completely read by the file receive adapter from the file system.|  
||Time to build batch|Average time taken by file receive adapter to build a batch.|  
|BizTalk:FILE Send Adapter|Bytes sent|Total number of bytes sent by the file send adapter. The counter is incremented only for messages that have been completely written to file system.|  
||Bytes sent/Sec|Number of bytes sent by the file send adapter per second. The counter applies only to messages that have been completely written to file system.|  
||Messages sent|Total number of messages sent by the file send adapter. The counter is incremented only for messages that have been completely written to file system.|  
||Messages sent/Sec|Number of messages sent by the file send adapter per second. The counter applies only to messages that have been completely written to file system.|  
  
## To access performance counters  
 Use the following steps to access the performance counters.  
  
#### If you are using Windows 2008  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.  
  
2.  In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.  
  
3.  In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:FILE** performance counter object and select the counters to be monitored  
  
4.  In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.  To select all available counter instances, select \<**All instances**\>.  
  
5.  After adding the counters, click **OK**.  
  
     The selected performance counters appear on the **Performance Monitor** screen.  
  
## See Also  
 [Planning for Sustained Performance](../core/planning-for-sustained-performance.md)