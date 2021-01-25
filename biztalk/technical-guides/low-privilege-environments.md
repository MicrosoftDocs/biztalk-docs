---
description: "Learn more about: Low-Privilege Environments"
title: "Low-Privilege Environments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: abdc45d0-b63a-4b6c-80c4-1f8e87644cd9
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Low-Privilege Environments
Several workflows that are included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack require elevated permissions to perform certain actions. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack enables you to perform basic monitoring functionalities in a low privilege environment. There are two Administrative Roles: the BizTalk Server Administrator, and the BizTalk Server Operator. The BizTalk Server Administrator is a high privilege role with access to configuration and tracking data. The BizTalk Server Administrator can perform all key administrative tasks such enlisting and starting artifacts. The BizTalk Server Operator is a low privilege role with access only to monitoring and troubleshooting actions. For more information, see [Minimum Security User Rights](https://technet.microsoft.com/library/aa559845\(BTS.80\).aspx).  
  
 Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack:  
  
-   Members of the BizTalk Server Operators group can do the following:  
  
    -   Monitor BizTalk Server for errors, query for suspended messages\instances, view configuration.  
  
    -   Monitor BizTalk Server installations and artifacts.  
  
    -   View service state and message flow.  
  
    -   Start or stop applications and artifacts such as orchestrations, send ports or send port groups that are in an enlisted state.  
  
    -   Enable or disable receive locations. The changes do not take effect until the next cache refresh interval of 60 seconds, which is the default. The cache refresh interval is set at the BizTalk Server group level.  
  
-   Members of the BizTalk Server Operators group cannot do the following:  
  
    -   Modify the configuration for BizTalk Server.  
  
    -   View message context properties classified as Personally Identifiable Information (PII) or message bodies.  
  
    -   Modify the course of message routing, such as removing or adding new subscriptions to the running system, including the ability to publish messages into the BizTalk Server runtime.  
  
> [!NOTE]  
>  To perform all monitoring tasks provided by the Management Pack such as restarting BTSNTSvc.exe service, you must be a member of the local Administrators group on the BizTalk Servers.  
  
## In this section  
  
-   [Monitoring](../technical-guides/monitoring.md)  
  
-   [Discoveries](../technical-guides/discoveries.md)
