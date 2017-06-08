---
title: "BizTalk Settings Dashboard, Group Page | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16e0ac35-49da-448c-b6d7-06e714d9e957
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Settings Dashboard, Group Page
Use the **Group** tab to modify the configuration of group-level performance settings in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  These settings are applicable for all the machines in a given group.  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Configuration refresh interval**|Set the interval in which [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] refreshes messaging configuration.|1 - 43200|-|  
|**Message Batch Threshold**|If the total size of an incoming message Batch exceeds this value, then it is split into smaller batches and processed.|1 - 10000000|102400|  
|**Large message size**|Set the threshold size of an individual message that triggers streaming in a batch and/or during transformations.|1 - 10000000|1000000|  

**Tracking and Reporting**

|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Message box performance counter sampling interval**|Set the interval at which performance counters are refreshed.<br /><br /> The interval trades off load on database versus up-to-dateness of counters. The higher value means less frequently updated data, and thus lesser load on the database.|1 – 1 – Maximum value of type Integer|-|  
|**Enable group level tracking**|Select this option to turn the group level tracking for BizTalk Server on.<br /><br /> Turning off global tracking disables the tracking interceptors for the entire [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group. This means, BizTalk Server will not track events in its tracking tables. **Note:**  This setting does not impact BAM Tracking.|On, Off|On|    
| **Allow import of tracking settings** | New starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. <br/><br/>When you import an application, the tracking settings configured on artifacts within the application are also imported. This is how all previous BizTalk versions behave. When unchecked, the tracking settings are not imported. This is a global setting, so it applies to all applications you import, and will import in the future. <br/><br/>If you want to control what is specifically tracked in your environments, just as you have in previous BizTalk versions, then leave this setting enabled. If you want to disable tracking on all artifacts on all imported applications, then uncheck this setting. <br/><br/>BTS task example: <br/>`btstask importbindings -ImportTrackingSettings:false -Source:c:\temp\binding.xml `| On, Off | On |   

**Restore, import, and export**

|Use this|To do this|
|--------------|----------------| 
|**Restore Defaults** |Click to cancel the modifications done, and apply the default BizTalk Server settings.| 
|**Import**|Import the group, host, and host instance settings that have been exported from another group. |
|**Export**|Export the group, host, and host instances settings from this current BizTalk group, to an XML file.| 
  
## See Also  
 [How to Modify Host Settings](../core/how-to-modify-host-settings.md)   
 [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md)