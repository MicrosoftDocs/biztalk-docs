---
description: "Learn more about: Communication Direction"
title: "Communication Direction"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Communication Direction
Each *port* has its own communication direction. The communication direction is used in combination with the communication pattern of the port's type to complete the definition of how a port can be used. The communication direction, or polarity, determines in which direction messages will be transmitted over that port.  
  
 If the port's type has a one-way communication pattern, its communication direction can be either Send or Receive. If the port's type has a two-way (request-response) communication pattern, its communication direction can be Send-Receive, in which a request is sent and a response is received, or Receive-Send, in which a request is received and a response is sent.  
  
## See Also  
 [Communication Pattern](../core/communication-pattern.md)  
 [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md)   
 [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md)
