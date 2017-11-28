---
title: "SOAP Adapter Performance Counters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40b54d4e-0a2e-483f-982a-97ab9fb59202
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SOAP Adapter Performance Counters
Performance counters allow you to monitor specific aspects of work performed on the site or system by service. Performance counters can help you identify and troubleshoot server performance issues.  
  
 The following performance counters are accessible for each host instance under the **BizTalk:SOAP Receive Adapter** and the **BizTalk:SOAP Send Adapter** performance object categories:  
  
|**Category**|**Counter**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:SOAP Receive Adapter|Messages received|Total number of messages received by the SOAP receive adapter. The counter is incremented after a request message is completely read by the adapter from the SOAP client.|  
||Messages received/Sec|Number of messages received by the SOAP receive adapter per second. The counter applies only to request messages that have been completely read by the adapter from the SOAP client.|  
|BizTalk:SOAP Send Adapter|Messages sent|Total number of messages sent by the SOAP send adapter. The counter is incremented only for messages that have reached the destination URL.|  
||Messages sent/Sec|Number of messages sent by the SOAP send adapter per second. The counter applies only to messages that have reached the destination URL.|  
  
## To access performance counters  
 Use the following steps to access the performance counters.  
  
#### If you are using Windows Server 2008  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.  
  
2.  In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.  
  
3.  In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:SOAP** performance counter object and select the counters to be monitored  
  
4.  In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**. To select all available counter instances, select \<**All instances**\>.  
  
5.  After adding the counters, click **OK**.  
  
     The selected performance counters appear on the **Performance Monitor** screen.