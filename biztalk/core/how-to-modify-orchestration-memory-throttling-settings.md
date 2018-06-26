---
title: "How to Modify Orchestration Memory Throttling Settings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Bts10.settings.HostInstanceOrchestration"
ms.assetid: f6953c68-7809-4518-87ec-e75c98884af3
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Modify Orchestration Memory Throttling Settings
The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host instance memory throttling mechanism continuously monitors for a throttling condition, calculates the severity of the throttling condition, and applies host instance memory throttling progressively depending on the calculated severity. This topic provides the step-by-step procedure to modify these settings using the Settings Dashboard.  

## Prerequisites  
 To perform this operation, you must be logged on as a member of the BizTalk Server Administrators group.  

### To modify the orchestration memory throttling settings of a host instance  

1. In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.  

2. In the **BizTalk Settings Dashboard** dialog box, on the **Host Instances** page, click the **Orchestration Memory Throttling** tab.  

3. Do the following, and then click **Apply** to apply the modifications and proceed to another tab. Or click **OK** to apply the modifications and exit the Settings Dashboard.  


   |     Use this      |                                                                                To do this                                                                                | Boundary values | Default value |
   |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|---------------|
   | **Host Instance** | From the drop-down box, select the running instance of a host on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime machine. |        -        |       -       |

    **Physical**  

   |Use this|To do this|Boundary values|Default value|  
   |--------------|----------------|---------------------|-------------------|  
   |**Optimal usage**|Specify the percentage of physical memory usage at which dehydration throttling comes into effect. This is the optimum percentage of physical memory to use for the host instances.|[0 – 100]|70|  
   |**Maximal usage**|Specify the percentage of physical memory usage at which dehydration throttling is maximum. This is the maximum percentage of physical memory to use for the host instances.<br /><br /> The minimum value of **Maximal usage** should be **Optimal usage**.|(Optimal usage – 100]<br /><br /> Except when both are 0 or 100.|85|  

    **Virtual**  

   |Use this|To do this|Boundary values|Default value|  
   |--------------|----------------|---------------------|-------------------|  
   |**Optimal usage**|Specify the percentage of virtual memory usage at which dehydration throttling comes into effect.<br /><br /> At this point, **TestThreshold** has the value **MaxThreshold** and any memory usage greater than **OptimalUsage** causes **TestThreshold** to be less than **MaxThreshold**.|[0 – 100]|65|  
   |**Maximal usage**|Specify the percentage of virtual memory usage at which dehydration throttling is maximum.<br /><br /> At this point, **TestThreshold** has the value **MinThreshold** and any memory usage less than **MaximalUsage** causes **TestThreshold** to be greater than **MinThreshold**.|(Optimal usage – 100]<br /><br /> Except when both are 0 or 100.|85|  

   > [!NOTE]
   >  To restore the default settings, click **Restore Defaults**.  

## See Also  
 [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md)