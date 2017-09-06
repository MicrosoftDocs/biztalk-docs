---
title: "MSMQ Adapter Performance Counters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab8b0342-c6c2-4113-ae54-359df28e5d30
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSMQ Adapter Performance Counters
Performance counters allow you to monitor specific aspects of work performed on the site or system by service. Performance counters can help you identify and troubleshoot server performance issues.  
  
 The following performance counters are accessible for each host instance under the **BizTalk:MSMQ Receive Adapter** and the **BizTalk:MSMQ Send Adapter** performance object categories:  
  
|**Category**|**Counter**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:MSMQ Receive Adapter|Bytes received|Total number of bytes received by the MSMQ receive adapter. The counter is incremented after a message is completely read by the MSMQ receive adapter from the source queue.|  
||Bytes received/Sec|Number of bytes received by the MSMQ receive adapter per second. The counter applies only to messages that have been completely read by the MSMQ receive adapter from the source queue.|  
||Messages received|Total number of messages received by the MSMQ receive adapter. The counter is incremented after a message is completely read by the MSMQ receive adapter from the source queue.|  
||Messages received/Sec|Number of messages received by the MSMQ receive adapter per second. The counter applies only to messages that have been completely read by the MSMQ receive adapter from the source queue.|  
|BizTalk:MSMQ Send Adapter|Bytes sent|Total number of bytes sent by the MSMQ send adapter. The counter is incremented only for messages that have reached the destination queue.|  
||Bytes sent/Sec|Number of bytes sent by the MSMQ send adapter per second. The counter applies only to messages that have reached the destination queue.|  
||Messages sent|Total number of messages sent by the MSMQ send adapter. The counter is incremented only for messages that have reached the destination queue.|  
||Messages sent/Sec|Number of messages sent by the MSMQ send adapter per second. The counter applies only to messages that have reached the destination queue.|  
  
## To access performance counters  
 Use the following steps to access the performance counters.  
  
#### If you are using Windows 2008  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.  
  
2.  In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.  
  
3.  In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:MSMQ** performance counter object and select the counters to be monitored  
  
4.  In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.  To select all available counter instances, select \<**All instances**>.  
  
5.  After adding the counters, click **OK**.  
  
     The selected performance counters appear on the **Performance Monitor** screen.  
  
## See Also  
 [Using LoadGen 2007 with MSMQ](../core/using-loadgen-2007-with-msmq.md)   
 [Optimizing Performance of the MSMQ Adapter](../core/optimizing-performance-of-the-msmq-adapter.md)