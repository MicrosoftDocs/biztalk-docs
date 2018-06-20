---
title: "How to Use Self-Correlating Direct Bound Ports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: feb651fa-3e35-4598-b229-335448f6919c
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use Self-Correlating Direct Bound Ports
Self-correlating direct bound ports are self referential. This means that a self-correlating direct bound port supplies the information that an orchestration can use to send messages back to its enclosing orchestration. When using the self-correlating direct binding, the orchestration engine generates a correlation token on a message that is particular to the orchestration instance. This provides the capability of getting messages back to a particular orchestration instance without using a correlation set.  
  
 For example, you can create a receiving self-correlating direct bound port in Orchestration A by specifying **Direct** for **Port binding** and selecting **Self Correlating** in the Port Configuration Wizard. Then, in Orchestration B, you declare a port as a Send Port Orchestration Parameter of the same port type as defined in Orchestration A. To do so, do the following:  
  
1. In the Orchestration View window, right-click **Orchestration Parameters**, and then click **New Port Parameter**.  
  
2. In the Properties window, for **Communication Direction**, select **Send**, and for **Port Type**, select the same port type as defined in Orchestration A.  
  
   This declaration creates a logical send port on the Port Surface in Orchestration Designer. Orchestration A calls Orchestration B using the **Start Orchestration** shape and passes the new port as a parameter, along with the other orchestration parameters, to Orchestration B. Orchestration B then performs its business logic and sends a message on the new port that was passed to it. The message is sent to the receiving self-correlating direct bound port of the instance of Orchestration A that started Orchestration B.  
  
   Although the preceding sequence of events can also be done with a **Call Orchestration** shape, it only makes sense when using a **Start Orchestration** shape. This is because when using a **Call Orchestration** shape, ports are passed by reference. The polarity of the port must be same in both of the orchestrations. Therefore, the communication direction of the port you pass in from one orchestration must be the same as the direction of the port reference in the called orchestration. However, when using the **Start Orchestration** shape, an asynchronous instantiation of an orchestration is generated and it cannot have **Out** or **Ref** parameters; therefore, the self-correlating direct bound port provides a way for an orchestration to respond back to the orchestration instance that instantiated it.  
  
   For an example of how to use self-correlating direct bound ports, see the SDK sample "Implementing Scatter and Gather Pattern" at [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## See Also  
 [How to Use MessageBox Direct Bound Ports](../core/how-to-use-messagebox-direct-bound-ports.md)   
 [How to Use Partner Orchestration Direct Bound Ports](../core/how-to-use-partner-orchestration-direct-bound-ports.md)