---
title: "Installing and Configuring BizTalk Server on the Orchestration Servers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BizTalk Server, installing on orchestration server"
  - "orchestration server, installing BizTalk Server"
ms.assetid: 72376a80-1377-4058-9478-fee668b804d0
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installing and Configuring BizTalk Server on the Orchestration Servers
This section describes how to install and configure BizTalk Server to be used as the orchestration server for running the Message Repair/New Submission orchestration and the FIN Repair and Reconciliation orchestration.  

### To install and configure BizTalk Server on the Orchestration Server  

1. Perform a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] choosing all the features except EDI, Human Workflow Services (HWS), and MRSR, unless required by other applications.  

   > [!NOTE]
   >  In the single-computer deployment, this computer is the same computer as the one that runs the HTTP front-end service and the BizTalk Messaging server.  

2. Perform configuration of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  

   > [!NOTE]
   >  Consider the following guidelines when configuring the BizTalk Orchestration servers:  

   - This server requires only one network adapter to connect it to the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer. It does not require another network adapter on the public side like the HTTP front-end server or the messaging server, and this makes it more secure against hacking attempts coming from the Internet or intranet/extranet.  

3. Install any additional hotfixes required by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as available in the installation guide.
