---
description: "Learn more about: Configuring the BizTalkApplicationServer and BizTalkServerIsolatedHost Hosts"
title: "Configuring the BizTalkApplicationServer and BizTalkServerIsolatedHost Hosts"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
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
