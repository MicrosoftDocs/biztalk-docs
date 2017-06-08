---
title: "BizTalk Settings Dashboard, Host Page, Rate Based Throttling Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c75659d-246f-4666-a62e-5c7ee7d777e9
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Settings Dashboard, Host Page, Rate Based Throttling Tab
Use the **Rate Based Throttling** tab to modify the settings of host instance that contain orchestrations or send adapters that receive and deliver or process messages that have been published to the MessageBox.  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Host**|From the drop-down box, select the host representing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime instances.|-|-|  
  
 **Publishing**  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Minimum number of samples**|Specify the minimum number of messages [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will sample for the **Sampling window duration** before considering rate-based throttling.<br /><br /> If the actual number of samples in a sampling window fall below this value, then the samples are discarded and throttling is not applied. This value should be consistent with a rate at which messages can be published under a medium load. For example, if your system is expected to handle 1,000 documents per second under a medium load, then this parameter should be set to 1,000 * Sample window duration in seconds. If the value is set too low, then the system may experience a throttling condition under low load. If the value is set too high, then there may not be enough samples for this technique to be effective.|1 – Max value of type Integer|100|  
|**Sampling window duration**|Specify the time-window (measured in seconds), which is used to calculate the publishing rate based on the samples collected. The duration should be increased if the latency required for publishing a single message is high.|1 – Max value of type Integer|15 sec|  
|**Rate overdrive factor**|Specify the percent to control how much higher you allow the request rate to be than the completion rate before a throttling condition occurs.<br /><br /> For example, if messages are being published at a rate of 200 per second and this parameter is set to 125, then the system allows the publication of up to 250 messages per second (125% * 200 = 250) before applying throttling. Specifying too small a value for this parameter can cause the system to throttle more aggressively and could lead to over-throttling. Specifying too large a value for this parameter can cause under throttling and prevent the throttling mechanism from recognizing a legitimate throttling condition.|1 – Max value of type Integer|125|  
|**Maximum throttling delay**|Specify the maximum delay (in seconds) [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] imposes on a message instance due to throttling. The actual delay depends on the severity of the throttling condition.|1 – Max value of type Integer|300 sec|  
|**Throttling override**|Specify if you want to override message publishing throttling.|0: Do not override<br /><br /> 1: Initiate throttling condition<br /><br /> 2: Do not throttle|0|  
|**Throttling override severity**|Specify the severity of an inbound throttling condition.<br /><br /> A higher value increases the severity of an inbound throttling condition initiated when **Throttling override** is set to 1.|1 – 1000|100|  
  
 **Delivery**  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Minimum number of samples**|Specify the minimum number of messages BizTalk Server will sample for the **Sampling window duration** before considering rate-based throttling.<br /><br /> If the actual number of samples in a sampling window falls below this value, then the samples are discarded and throttling is not applied. This value should be consistent with a rate at which messages can be delivered under a medium load. For example, if your system is expected to handle 1,000 documents per second under a medium load, then this parameter should be set to 1,000 * Sample window duration in seconds.<br /><br /> If the value is set too low, then the system may experience a throttling condition under low load. If the value is set too high, then there may not be enough samples for this technique to be effective.|1 – Max value of type Integer|100|  
|**Sampling window duration**|Specify the time-window (in seconds), which is used to calculate the processing rate based on the samples collected. The duration should be increased if the latency required for processing a single message is high.|1 – Max value of type Integer|15 sec|  
|**Rate overdrive factor**|Specify the percent to control how much higher you allow the delivery rate to the Orchestration or Messaging engine to be than the completion rate before a throttling condition occurs.<br /><br /> For example, if messages are being processed at a rate of 200 per second and this parameter is set to 125, then the system allows the processing of up to 250 messages per second (125% * 200 = 250) before applying throttling. Specifying too small a value for this parameter causes the system to throttle more aggressively and could lead to over throttling. Specifying too large a value for this parameter causes under throttling and prevent the throttling mechanism from recognizing a legitimate throttling condition.|1 – Max value of type Integer|125|  
|**Maximum throttling delay**|Specify the maximum delay [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] imposes on a message instance due to throttling. The actual delay depends on the severity of the throttling condition.|1 – Max value of type Integer|300 sec|  
|**Throttling override**|Specify if you want to override message delivery throttling.|0: Do not override<br /><br /> 1: Initiate throttling condition<br /><br /> 2: Do not throttle|0|  
|**Throttling override severity**|Specify the severity of the outbound throttling condition.<br /><br /> A higher value increases the severity of an outbound throttling condition initiated when **Throttling override** is set to 1.|1 – 1000|100|  
|**Restore Defaults**|Click to cancel the modifications and apply the default BizTalk Server settings.|-|-|  
  
## See Also  
 [How to Modify Group Settings](../core/how-to-modify-group-settings.md)   
 [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md)