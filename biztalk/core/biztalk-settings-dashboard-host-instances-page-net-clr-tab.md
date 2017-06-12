---
title: "BizTalk Settings Dashboard, Host Instances Page, .NET CLR Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 050dc059-31e2-4eb2-9367-4af55da81a58
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Settings Dashboard, Host Instances Page, .NET CLR Tab
When you need to update the number of Windows threads available in the .NET thread pool associated with an instance of a BizTalk host, use the **.NET CLR** tab to modify the appropriate CLR Hosting values in the registry of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Host Instance**|From the drop-down box, select the running instance of a host on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime machine.|-|-|  
|**Threading Settings**||-|-|  
|**Max. worker threads**|Specify the maximum number of .NET CLR worker threads.|[Min worker threads, 500]|25|  
|**Min. worker threads**|Specify the minimum number of .NET CLR worker threads.|[0, 500]|5|  
|**Max. IO threads**|Specify the maximum number of IO threads.|[Min IO threads, 1000]|250|  
|**Min. IO threads**|Specify the minimum number of IO threads.|[0, 1000]|25|  
|**Restore Defaults**|Click to cancel the modifications done and apply the default BizTalk Server settings.|-|-|  
  
## See Also  
 [How to Modify Group Settings](../core/how-to-modify-group-settings.md)   
 [How to Modify Host Settings](../core/how-to-modify-host-settings.md)