---
title: "Configuring the BizTalkApplicationServer and BizTalkServerIsolatedHost Hosts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring, hosts"
  - "BizTalkApplicationServer host"
  - "hosts"
  - "BizTalkServerIsolatedHost host"
ms.assetid: 17bc9f01-ff87-427d-8411-6a065814ba1e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring the BizTalkApplicationServer and BizTalkServerIsolatedHost Hosts
To limit the messaging (sending and receiving messages) to the BizTalk Messaging servers, you need to configure the default hosts, which are running the MSMQT send and receive handlers, to run only on the messaging servers.  
  
### To configure the default hosts  
  
1.  Using the BizTalk Administration Console, delete the orchestration servers host instances from the BizTalkApplicationServer host:  
  
    -   Right-click each host instance and click **Stop**.  
  
    -   Right-click each host instance and click **Delete**.  
  
2.  Using the BizTalk Administration Console, delete the orchestration servers host instances from the BizTalkServerIsolatedHost host:  
  
    -   Right-click each host instance and click Delete.  
  
3.  After you have configured the hosts, restart all the host instances on all the servers.