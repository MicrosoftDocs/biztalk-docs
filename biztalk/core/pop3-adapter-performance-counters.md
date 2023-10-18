---
description: "Learn more about: POP3 Adapter Performance Counters"
title: "POP3 Adapter Performance Counters"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# POP3 Adapter Performance Counters
Performance counters allow you to monitor specific aspects of work performed on the site or system by service. Performance counters can help you identify and troubleshoot server performance issues.  
  
 The following performance counters are accessible for each host instance under the **BizTalk:POP3 Receive Adapter** performance object category:  
  
|**Category**|**Counter**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:POP3 Receive Adapter|Active sessions|Number of open POP3 connections the POP3 adapter is managing at a time.|  
||Bytes received|Total number of bytes downloaded by the POP3 adapter from a mail server.|  
||Bytes receive/Sec|Number of bytes downloaded by the POP3 adapter from a mail server per second.|  
||Messages received|Total number of email messages downloaded by the POP3 adapter from a mail server.|  
||Messages received/Sec|Number of email messages downloaded by the POP3 adapter from mail server per second.|  
  
## To access performance counters  
 Follow these steps to access performance counters for the POP3 adapter:  
  
#### If you are using Windows 2008  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.  
  
2.  In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.  
  
3.  In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:POP3 Receive Adapter** performance counter object and select the counters to be monitored  
  
4.  In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.  To select all available counter instances, select \<**All instances**\>.  
  
5.  After adding the counters, click **OK**.  
  
     The selected performance counters appear on the **Performance Monitor** screen.  
  
## See Also  
 [Monitoring BizTalk Server](../core/monitoring-biztalk-server.md)  
 [Processing Multi Part Messages with the POP3 Adapter](../core/processing-multi-part-messages-with-the-pop3-adapter.md)   
 [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)
