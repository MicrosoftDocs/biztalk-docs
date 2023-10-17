---
description: "Learn more about: Tracking Data Decode Services Performance Counters"
title: "Tracking Data Decode Services Performance Counters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 733450b1-71b5-48a4-9ac3-cd880324440c
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tracking Data Decode Services Performance Counters
Performance counters allow you to monitor specific aspects of work performed on the site or system by service. Performance counters can help you identify and troubleshoot server performance issues.  
  
 The following performance counters are accessible for each host instance under the **BizTalk:TDDS** performance object category:  
  
|**Category**|**Counter**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:TDDS|Batches being processed|The number of batches that are being processed inside the current SQL transaction.|  
||Batches committed|The number of batches committed to the destination database.|  
||Events being processed|The number of events that are being processed inside of the current SQL transaction.|  
||Event Committed|The number of events committed to the destination database within this second.|  
||Records being processed|The number of records that are being processed inside the current SQL transaction.|  
||Records Committed|The number of records committed to the destination database during this second.|  
||Total Batches|Total batches processed by TDDS.|  
||Total Events|Total events processed by TDDS.|  
||Total Failed Batches|Total batches failed to run by TDDS.|  
||Total Failed Events|Total events failed to run by TDDS.|  
||Total Records|Total records processed by TDDS.|  
  
## To access performance counters  
 Use the following steps to access the performance counters.  
  
#### If you are using Windows 2008  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.  
  
2.  In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.  
  
3.  In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:TDDS** performance counter object and select the counters to be monitored  
  
4.  In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.  To select all available counter instances, select \<**All instances**\>.  
  
5.  After adding the counters, click **OK**.  
  
     The selected performance counters appear on the **Performance Monitor** screen.  
  
## See Also  
 [Performance Tips and Tricks](../core/performance-tips-and-tricks.md)   
 [Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Optimizing Resource Usage Through Host Throttling](../core/optimizing-resource-usage-through-host-throttling.md)
