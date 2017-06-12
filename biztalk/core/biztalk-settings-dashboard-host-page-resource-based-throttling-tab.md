---
title: "BizTalk Settings Dashboard, Host Page, Resource Based Throttling Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c37d700d-5fe6-4f31-97ae-92e0bcbc3589
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Settings Dashboard, Host Page, Resource Based Throttling Tab
Use the **Resource Based Throttling** tab to manage the usage of system resources (such as threads, memory, and database size) by a host instance process.  
  
|**Use this**|To do this|Boundary values|Default value|  
|------------------|----------------|---------------------|-------------------|  
|**Host**|From the drop-down list, select the host representing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime instances.|-|-|  
|**Per CPU Settings**||-|-|  
|**Threads**|Specify the maximum number of threads in the process (per CPU) allowed before the throttling begins.|[0, Maximum value of type Integer)|0|  
|**Database connections**|Specify the maximum number of database sessions (per CPU) allowed before throttling begins.|1 – Maximum value of type Integer|0|  
|**In-process messages**|Specify the maximum number of messages delivered to the End Point Manager (EPM) or XLANG that have not been processed. This does not include the messages retrieved from database but still waiting for delivery in the in-memory queue.|1 – Maximum value of type Integer|1000|  
|**Internal message queue size**|Indicate the size of the in-memory queue. This queue serves as a temporary placeholder for delivering messages.<br /><br /> Setting a large value for this parameter may improve low-latency scenarios to some extent since more messages will be proactively retrieved from the MessageBox database for processing. Since the messages in this queue consume memory, setting this parameter to a smaller value may be desirable for scenarios involving large messages in order to avoid memory based throttling of the process. **Note:**  If you modify this value, the host needs to be restarted for the change to take effect.|1 – Maximum value of type Integer|100|  
|**Message count in DB**|Indicate the total number of messages published by the host instance to the work, state, and suspended queues of the subscribing hosts.<br /><br /> The **Message count in DB** setting also indirectly defines the threshold for a throttling condition based on the number of messages in the spool table or tracking table. If the number of messages in the spool table or tracking table exceeds 10 times this value then a throttling condition will be triggered.|1 – Maximum value of type Integer|50000|  
|**Memory Usage**||-|-|  
|**Global physical**|Specify (in percent) the maximum system-wide virtual memory usage allowed before throttling begins.|0: disable<br /><br /> 1% – 100%<br /><br /> Values > 100% are treated as MBs and can go up to int Max|0|  
|**Process virtual**|Specify the maximum process memory (in percent) allowed before throttling begins (in percent or megabytes).|0: disable<br /><br /> 1% – 100%<br /><br /> Values > 100% are treated as MBs and can go up to int Max|25|  
|**Spool multiplier**|Indicate the factor by which the **Message count in DB** threshold is multiplied and then compared against the current record count in the spool table.<br /><br /> This is done to determine whether the system should throttle on spool table size. If this value is set to 0, spool table size is not used as a consideration for determining a throttling condition.|0-1000|10|  
|**Tracking data multiplier**|Specify the factor by which the **Message count in DB** threshold is multiplied and then compared against the current record count in the tracking table.<br /><br /> This is done to determine whether the system should throttle on tracking table size. If this value is set to 0, tracking table size is not used as a consideration for determining a throttling condition.|0-1000|10|  
|**Limit to trigger GC**|Specifies when a .NET garbage collection (GC) is triggered as process memory consumption increases and approaches the threshold. When the memory consumption exceeds this percentage value of the memory threshold, a GC is triggered.|50-100|80|  
|**Batch memory threshold**|Indicate (in percent) the memory threshold beyond which to throttle the publishing of a batch of messages.<br /><br /> The batch memory threshold is computed by multiplying this percentage factor by the **Process virtual** threshold. If the memory estimated to execute a publishing batch exceeds the batch memory threshold, the batch is subject to process memory based throttling. Otherwise, the batch is exempted from process memory based throttling even when the total process memory exceeds the **Process virtual** threshold.<br /><br /> A value of zero indicates that all publishing batches may be subject to process memory based throttling even if the memory estimated to execute the batch is minimal.|0%-100%|1|  
|**Severity**||-|-|  
|**Memory**|Indicate the severity of a process memory triggered throttling condition. Specified in percentage value, this parameter sets the severity of a throttling condition caused when the **Process virtual** threshold is exceeded.|1 – 1000|500|  
|**DB size**|Indicate the severity of a database sized triggered throttling condition. Specified in percentage value, this parameter sets the severity of a throttling condition caused when the **Message count in DB** threshold is exceeded.|1 – 1000|1|  
|**Inflight message**|Specify the reaction time of throttling when the value for **In-process messages** exceeds the threshold. This is specified in percentage value and this parameter sets the severity of a throttling condition caused when the value for **In-process messages** threshold is exceeded.|1 – 1000|75|  
|**Restore Defaults**|Click to cancel the modifications done and apply the default BizTalk settings.|-|-|  
  
## See Also  
 [How to Modify Group Settings](../core/how-to-modify-group-settings.md)   
 [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md)