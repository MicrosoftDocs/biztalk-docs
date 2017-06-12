---
title: "BizTalk Settings Dashboard, Host Page, Orchestrations Throttling Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f0541d6-b20d-4b9d-983c-a230475922ce
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Settings Dashboard, Host Page, Orchestrations Throttling Tab
Use the **Orchestrations Throttling** tab to modify the orchestration throttling settings and limiting the number of outstanding messages it can have. This prevents an orchestration from consuming too much memory.  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Host**|From the drop-down box, select the host representing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime instances.|-|-|  
|**Dehydration behavior**|Select the dehydration behavior of the orchestration (XLANG) engine. Note that the other XLANG settings are editable only if you select “Custom”.<br /><br /> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the dehydration properties to decide when to dehydrate and rehydrate orchestrations. Under normal load, the default dehydration values are sufficient, but if you are running under heavy load and want to change the performance characteristics, you should tune the values. The dehydration behavior of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] depends entirely on how much memory is available and how much memory is being used.|Always<br /><br /> Never<br /><br /> Custom|Custom|  
  
 **Time Based**  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Maximum threshold**|Specify the maximum idle time an orchestration instance could be blocked before being dehydrated.|(MinThreshold – Maximum value of type Integer]|1800 sec|  
|**Minimum threshold**|Specify the minimum idle time an orchestration instance could be blocked before being dehydrated.|[1 – Maximum value of type Integer|1sec|  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Subscriptions**|Select this option to manually set the ‘pause at’ and ‘resume at’ values for a subscription. By default, the system takes care of the subscriptions at runtime.|On, Off|Off|  
|**Pause at**|Specify the maximum number of messages you want a subscription to store.<br /><br /> When a subscription has messages waiting to be consumed that are greater than or equal to the specified number, the messages are not delivered to the subscription instance. The minimum number of messages would be the ‘resume at’ value.<br /><br /> For example, if you set **Pause at** value to 100, it means an orchestration has 100 outstanding messages and the MessageBox will stop sending additional messages.|(ResumeAt – Maximum value of type Integer]. Except when both are 0.|Off|  
|**Resume at**|Specify the number of messages you want the MessageBox to resume sending messages to subscription.<br /><br /> For example, set the **Resume at** value to 50. When the orchestration's number of outstanding messages is down to 50, it specifies that MessageBox can resume sending messages.|[0 – Maximum value of type Integer)|Off|  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Restore Defaults**|Click to cancel the modifications done and apply the default BizTalk Server settings.|-|-|  
  
## See Also  
 [How to Modify Group Settings](../core/how-to-modify-group-settings.md)   
 [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md)