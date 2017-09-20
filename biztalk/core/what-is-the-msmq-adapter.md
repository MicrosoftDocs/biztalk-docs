---
title: "What Is the MSMQ Adapter? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSMQ adapters, about MSMQ adapters"
  - "MSMQ adapters"
ms.assetid: 4f4bfe49-19fc-4195-8826-0329f17cbe94
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is the MSMQ Adapter?
With the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Adapter for MSMQ (the MSMQ adapter), you can send and receive messages to Microsoft Message Queuing (also known as MSMQ) queues using Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The MSMQ adapter supports Message Queuing 4.0. The adapter works with transactional and non-transactional, public and private, and local and remote queues. Additionally, the MSMQ adapter provides large (greater than 4 MB) message support and gives you access to Message Queuing 4.0 features such as remote transactional reads and reading from subqueues.  
  
 If you have upgraded your BizTalk Server installation to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], the BizTalk Server 2009 Adapter for MSMQ is not removed. Because [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installs a new version of the MSMQ adapter, you can safely uninstall the BizTalk Server 2009 Adapter for MSMQ and then manually remove the directory structure for this version of the adapter.