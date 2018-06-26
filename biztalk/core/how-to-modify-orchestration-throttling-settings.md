---
title: "How to Modify Orchestration Throttling Settings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Bts10.settings.HostOrchestration"
ms.assetid: 30086994-cb55-4ff7-9940-df197e5e35ce
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Modify Orchestration Throttling Settings
Using the BizTalk Settings Dashboard, you can modify the orchestration throttling configuration settings of a given host, across the BizTalk Group. These settings apply to all host instances assigned to the given host. This topic provides the step-by-step procedure to modify these settings.  

 The orchestration throttling settings, specified in the **btsntsvc.exe.config** file, prevent an orchestration from consuming too much memory by limiting the number of outstanding messages it can have. All messages continue to be delivered to the MessageBox; however, queued messages are not delivered to the orchestration until it processes some of its outstanding messages.  

## Prerequisites  
 To perform this operation, you must be logged on as a member of the BizTalk Server Administrators group.  

### To modify the orchestrations throttling settings of a host  

1. In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.  

2. In the **BizTalk Settings Dashboard** dialog box, on the **Hosts** tab, click the **Orchestrations Throttling** tab.  

3. Do the following, and then click **Apply** to apply the modifications and proceed to another tab. Or click **OK** to apply the modifications and exit the Settings Dashboard.  


   |         Use this         |                                                                                                                                                                                                                                                                                                                                                               To do this                                                                                                                                                                                                                                                                                                                                                                |               Boundary values               | Default value | Upgrade logic |
   |--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------|---------------|---------------|
   |         **Host**         |                                                                                                                                                                                                                                                                                     From the drop-down list, select the host representing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime instances.                                                                                                                                                                                                                                                                                     |                      -                      |       -       |       -       |
   | **Dehydration behavior** | Select the dehydration behavior of the orchestration (XLANG) engine. Note that the other XLANG settings are editable only if you select “Custom”.<br /><br /> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the dehydration properties to decide when to dehydrate and rehydrate orchestrations. Under normal load, the default dehydration values are sufficient, but if you are running under heavy load and want to change the performance characteristics, you should tune the values. The dehydration behavior of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] depends entirely on how much memory is available and how much memory is being used. | Always<br /><br /> Never<br /><br /> Custom |    Custom     |       -       |

    **Time Based**  

   |Use this|To do this|Boundary values|Default value|Upgrade logic|  
   |--------------|----------------|---------------------|-------------------|-------------------|  
   |**Maximum threshold**|Specify the maximum idle time an orchestration instance could be blocked before being dehydrated.|(MinThreshold – Maximum value of type Integer]|1800 sec|-|  
   |**Minimum threshold**|Specify the minimum idle time an orchestration instance could be blocked before being dehydrated.|[1 – Maximum value of type Integer)|1 sec|-|  
   |**Subscriptions**|Select this option to manually set the ‘pause at’ and ‘resume at’ values for a subscription. By default, the system takes care of the subscriptions at runtime.|On, Off|Off|-|  
   |**Pause at**|Specify the maximum number of messages you want a subscription to store.<br /><br /> When a subscription has messages waiting to be consumed that are greater than or equal to the specified number, the messages are not delivered to the subscription instance. The minimum number of messages would be the ‘resume at’ value.<br /><br /> For example, if you set **Pause at** value to 100, it means an orchestration has 100 outstanding messages and the MessageBox will stop sending additional messages.|(ResumeAt – Maximum value of type Integer].<br /><br /> Except when both are 0.|Off|-|  
   |**Resume at**|Specify the number of messages you want the MessageBox to resume sending messages to subscription.<br /><br /> For example, set the **Resume at** value to 50. When the orchestration's number of outstanding messages is down to 50, it specifies that MessageBox can resume sending messages.|[0 – Maximum value of type Integer)|Off|-|  

   > [!NOTE]
   >  To restore the default settings, click **Restore Defaults**.  

## See Also  
 [How to Modify Host Settings](../core/how-to-modify-host-settings.md)