---
title: "BizTalk Settings Dashboard, Host Instances Page, Orchestration Memory Throttling Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1686113-09b0-402b-876d-b8fd058bcdb0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Settings Dashboard, Host Instances Page, Orchestration Memory Throttling Tab
Use the **Orchestration Memory Throttling** tab to continuously monitor for a throttling condition, calculate the severity of the throttling condition, and apply host instance memory throttling progressively depending on the calculated severity.  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Host Instance**|From the drop-down box, select the running instance of a host on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime machine.|-|-|  
  
 **Physical**  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Optimal usage**|Specify the percentage of physical memory usage at which dehydration throttling comes into effect. This is the optimum percentage of physical memory to use for the host instances.|[0 – 100]|70|  
|**Maximal usage**|Specify the percentage of physical memory usage at which dehydration throttling is maximum. This is the maximum percentage of physical memory to use for the host instances.<br /><br /> The minimum value of maximal usage should be **Optimal usage**.|(Optimal usage – 100]<br /><br /> Except when both are 0 or 100.|85|  
  
 **Virtual**  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Optimal usage**|Specify the percentage of virtual memory usage at which dehydration throttling comes into effect.<br /><br /> At this point, **TestThreshold** has the value **MaxThreshold** and any memory usage greater than **OptimalUsage** causes **TestThreshold** to be less than **MaxThreshold**.|[0 – 100]|65|  
|**Maximal usage**|Specify the percentage of virtual memory usage at which dehydration throttling is maximum.<br /><br /> At this point, **TestThreshold** has the value **MinThreshold** and any memory usage less than **MaximalUsage** causes **TestThreshold** to be greater than **MinThreshold**.|(Optimal usage – 100]<br /><br /> Except when both are 0 or 100.|85|  
|**Restore Defaults**|Click to cancel the modifications done and apply the default BizTalk Server settings.|-|-|  
  
## See Also  
 [How to Modify Group Settings](../core/how-to-modify-group-settings.md)   
 [How to Modify Host Settings](../core/how-to-modify-host-settings.md)