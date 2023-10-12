---
description: "Learn more about: Message Box Performance Counters"
title: "Message Box Performance Counters"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Message Box Performance Counters
Performance counters allow you to monitor specific aspects of work performed on the site or system by service. Performance counters can help you identify and troubleshoot server performance issues.  
  
 The following performance counters are accessible for each host instance under the **BizTalk:Message Box:General Counters** and the **BizTalk:Message Box:Host Counters** performance object categories:  
  
> [!NOTE]
>  To enable counters that refer to the SQL Agent job, you must include the role SQLAgentUserRole to the service account used to run the BizTalk host/NT Service. Alternatively, you can grant permission using other roles or by granting explicit permission to read the MSDB database.  
  
> [!NOTE]
>  If you have added a new MessageBox to your BizTalk Server group, the counters listed below will not be available for the new MessageBox until the configured **Cache Refresh** interval for the BizTalk Server group has elapsed (default of 60 seconds).  
  
|Category|Counter|Description|  
|--------------|-------------|-----------------|  
|General Counters|Instances-Total Number|Tracks the sum of all the instances of each host, which exist within a particular Message Box.|  
|General Counters|MsgBox Dead Processes Cleanup (Purge Jobs)|Time in seconds for most recent run of SQL agent job which releases database rows associated with dead BizTalk processes.|  
|General Counters|MsgBox Msg Cleanup (Purge Jobs)|Time in seconds for most recent run of SQL agent job which cleans up message box tables associated with removed messages.|  
|General Counters|MsgBox Parts Cleanup (Purge Jobs)|Time in seconds for most recent run of SQL agent job which clean up message box tables associated with removed message parts.|  
|General Counters|MsgBox Purge Subscriptions Job (Purge Jobs)|Time in seconds for most recent run of SQL agent job which purges subscriptions which are no longer in use.|  
|General Counters|Spool Size|Tracks the size of the spool on a particular message box on a particular server.|  
|General Counters|Tracked Msgs Copy (Purge Jobs)|Time in seconds for most recent run of SQL agent job which copies tracked message bodies for tracked messages.|  
|General Counters|Tracking data size|Tracks the size of the tracking data table on a particular message box on a particular server.|  
|General Counters|Tracking Spool Cleanup (Purge Jobs)|Time in seconds for the most recent run of the SQL agent job which purges the inactive tracking spool tables.|  
|Host Counters|Host Queue - Instance State Msg Refs - Length|Tracks the number of message references in the instance state queue for this particular host.|  
|Host Counters|Host Queue - Length|Tracks the total number of messages in the particular host queue.|  
|Host Counters|Host Queue - Number of Instances|Tracks the number of instances of this particular host.|  
|Host Counters|Host Queue - Suspended Msgs - Length|Tracks the total number of suspended messages for the particular host.|  
  
## To access performance counters  
 Use the following steps to access the performance counters.  
  
#### If you are using Windows 2008  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.  
  
2.  In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.  
  
3.  In the **Add Counters** dialog box, from the **Available Counters** list, select either **BizTalk:Message Box:General Counters** or  **BizTalk:Message box:Host Counters**. Expand the selected performance counter object and select the counters to be monitored  
  
4.  In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.  To select all available counter instances, select \<**All instances**\>.  
  
5.  After adding the counters, click **OK**.  
  
     The selected performance counters appear on the **Performance Monitor** screen.  
  
## See Also  
 [Performance Tips and Tricks](../core/performance-tips-and-tricks.md)   
 [Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Optimizing Resource Usage Through Host Throttling](../core/optimizing-resource-usage-through-host-throttling.md)
