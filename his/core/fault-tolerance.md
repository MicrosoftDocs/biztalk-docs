---
title: "Fault Tolerance | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7356f533-d1d5-40d6-8029-e3e92bd50fcf
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Fault Tolerance
The total number of sessions per server and total number of servers will need to take into account the fault tolerance requirements.  Host Integration Server supports a logical grouping of servers called a sub-domain.  Clients are configured for a particular sub-domain and can access resources on any server in that sub-domain.  By increasing the number of server over which the sessions are spread, you reduce the amount of capacity lost when one server fails.  For example if you need to support 10,000 sessions, dividing them between two servers mean a 50% loss of capacity if one server fails.  If these are spread across four servers then the loss of one server only reduces the capacity by 25%.  
  
 In addition, these servers can be overloaded to provide redundancy.  Using the example above, you could place 7,500 sessions on two servers.  In this case the loss of one server will only reduces the capacity by 25%.  With this strategy you can provide 100% redundancy.