---
title: "Manage Send Ports and Send Port Groups | Microsoft Docs"
description: Links to create, configure, enlist, unenlist, and start and stop send ports in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: db45f9f9-b32a-4b9c-a3bf-8c271d0f0cf9
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Manage Send Ports and Send Port Groups

## Overview
This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to create, configure, and manage send ports and send port groups in a BizTalk application. A send port specifies the location to which messages are sent and optionally responses are received. Any time a message is sent to a send port, a new instance of the send port service is created, which is called a *service instance*.  
  
 A send port group is a logical grouping of send ports. When a message is sent to a send port group, it is routed to all of the associated send ports.  For background information about send ports and send port groups, see [Send Ports and Send Port Groups](../core/send-ports-and-send-port-groups.md).  
  
> [!NOTE]
>  You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
> 
> [!NOTE]
>  While developing a BizTalk application, the developer can use BizTalk design tools in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], such as Orchestration Designer, to create and configure send ports and send port groups. For more information, see [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md).  
  
## Next steps
  
-   [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)  
  
-   [Creating and Configuring Send Port Groups](../core/creating-and-configuring-send-port-groups.md)  
  
-   [Enlist a Send Port or Send Port Group](../core/how-to-enlist-a-send-port-or-send-port-group.md)  
  
-   [Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md)  
  
-   [Start a Send Port or Send Port Group](../core/how-to-start-a-send-port-or-send-port-group.md)  
  
-   [Stop a Send Port or Send Port Group](../core/how-to-stop-a-send-port-or-send-port-group.md)