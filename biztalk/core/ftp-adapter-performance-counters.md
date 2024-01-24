---
description: "Learn more about: FTP Adapter Performance Counters"
title: "FTP Adapter Performance Counters"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# FTP Adapter Performance Counters
Performance counters allow you to monitor specific aspects of work performed on the site or system by service. Performance counters can help you identify and troubleshoot server performance issues.  
  
 The following performance counters are accessible for each host instance under the **BizTalk:FTP Receive Adapter** and the **BizTalk:FTP Send Adapter** performance object categories:  
  
|**Category**|**Counter**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:FTP Receive Adapter|Bytes received|Total number of bytes received by the FTP receive adapter. The counter is incremented after a message is completely read by the FTP receive adapter from the FTP server.|  
||Bytes received/Sec|Number of bytes received by the FTP receive adapter per second. The counter applies only to messages that have been completely read by the FTP receive adapter from the FTP server.|  
||Messages received|Total number of messages received by the FTP receive adapter. The counter is incremented after a message is completely read by the FTP receive adapter from the FTP server.|  
||Messages received/Sec|Number of messages received by the FTP receive adapter per second. The counter applies only to messages that have been completely read by the FTP receive adapter from the FTP server.|  
|BizTalk:FTP Send Adapter|Bytes sent|Total number of bytes sent by the FTP send adapter. The counter is incremented only for messages that have been written to the destination FTP server.|  
||Bytes sent/Sec|Number of bytes sent by the FTP send adapter per second. The counter applies only to messages that have been written to the destination FTP server.|  
||Messages sent|Total number of messages sent by the FTP send adapter. The counter is incremented only for messages that have been written to the destination FTP server.|  
||Messages sent/Sec|Number of messages sent by the FTP send adapter per second. The counter applies only to messages that have been written to destination FTP server.|  
  
## To access performance counters  
 Use the following steps to access the performance counters.  
  
#### If you are using Windows 2008  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.  
  
2.  In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.  
  
3.  In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:FTP** performance counter object and select the counters to be monitored  
  
4.  In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.  To select all available counter instances, select \<**All instances**\>.  
  
5.  After adding the counters, click **OK**.  
  
     The selected performance counters appear on the **Performance Monitor** screen.  
  
## See Also  
 [Monitoring BizTalk Server](../core/monitoring-biztalk-server.md)
 [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)
