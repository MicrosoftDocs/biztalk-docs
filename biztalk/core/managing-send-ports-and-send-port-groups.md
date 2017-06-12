---
title: "Managing Send Ports and Send Port Groups | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [send ports], about managing send ports"
  - "managing [send port groups]"
  - "send port groups, managing"
  - "managing [send ports]"
  - "managing [send port groups], about managing send port groups"
  - "send ports, managing"
ms.assetid: db45f9f9-b32a-4b9c-a3bf-8c271d0f0cf9
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing Send Ports and Send Port Groups
This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to create, configure, and manage send ports and send port groups in a BizTalk application. A send port specifies the location to which messages are sent and optionally responses are received. Any time a message is sent to a send port, a new instance of the send port service is created, which is called a *service instance*.  
  
 A send port group is a logical grouping of send ports. When a message is sent to a send port group, it is routed to all of the associated send ports.  For background information about send ports and send port groups, see [Send Ports and Send Port Groups](../core/send-ports-and-send-port-groups.md).  
  
> [!NOTE]
>  You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see [WMI Class Reference](../core/wmi-class-reference.md).  
  
> [!NOTE]
>  While developing a BizTalk application, the developer can use BizTalk design tools in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], such as Orchestration Designer, to create and configure send ports and send port groups. For more information, see [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md).  
  
## In This Section  
  
-   [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)  
  
-   [Creating and Configuring Send Port Groups](../core/creating-and-configuring-send-port-groups.md)  
  
-   [How to Enlist a Send Port or Send Port Group](../core/how-to-enlist-a-send-port-or-send-port-group.md)  
  
-   [How to Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md)  
  
-   [How to Start a Send Port or Send Port Group](../core/how-to-start-a-send-port-or-send-port-group.md)  
  
-   [How to Stop a Send Port or Send Port Group](../core/how-to-stop-a-send-port-or-send-port-group.md)