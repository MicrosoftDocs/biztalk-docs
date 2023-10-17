---
description: "Learn more about: Host Internal Response Time"
title: "Host Internal Response Time1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9b5a62c-ae1e-4c02-b7c4-966682d8806c
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Host Internal Response Time
The host internal response time is the time that the transactions spend inside the host system processing the transaction requests from Transaction Integrator (TI). These include components such as processing the business logic, disk and database I/O, and handling the two-phase commit (2PC) processing.  
  
 One way to get an indication of the host internal transaction processing performance is to run the transactions under load without the TI and computer components. A typical goal for an interactive transaction is to keep the response time at 500 ms and less than one second for most part of the daily load conditions. This is a tough goal, and many systems under ordinary operational loads have hard times maintaining this. There is a section dedicated to analyzing the effects on the application server in case the response times get longer.  
  
## See Also  
 [Major Elements Affecting Overall Performance](../core/major-elements-affecting-overall-performance1.md)
