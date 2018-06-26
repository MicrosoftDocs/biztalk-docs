---
title: "Task Order2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78ee8621-614c-4945-89ac-00f8e0b878c8
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Task Order
Just as with the SNA Manager, configuration tasks must be carried out in a certain order with the command-line interface. For example, before configuring an LU, you must configure the connection that the LU will use. You can vary the interface you use for each configuration task, as long as you carry out the tasks in order, and as long as you have already installed [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] with the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Setup and then run the SNA Manager. For example, you can carry out tasks using the SNA Manager, then the command-line interface, then the SNA Manager again, as long as the tasks are done in the correct order.  
  
 The following table shows the order in which configuration tasks must be carried out, and the command used to carry out the task.  
  
## Task Order for Configuration Tasks  
  
|                                        Configuration task (in order)                                         |                                 Command that carries out task                                 |
|--------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
|                                      Add a server to the configuration                                       |                                     **snacfg server\\**\*                                     |
|                                 Configure link service(s) for the server(s)                                  |                                      **snacfg link\\**\*                                      |
|                                  Configure connection(s) for the server(s)                                   |                                     **snacfg connection**                                     |
|                                    Configure LU(s) for the connection(s)                                     | **snacfg appcllu**,  **snacfg appcrlu**,  **snacfg lu**,  **snacfg lua**,  or  **snacfg lud** |
|                                        Create LU pool(s)  (optional)                                         |                   **snacfg pool**,  **snacfg poola**,  or  **snacfg poold**                   |
|                                      Assign LUs to pool(s)  (optional)                                       |                      **snacfg lu**,  **snacfg lua**,  or  **snacfg lud**                      |
| Add users to the list used by [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] |                                      **snacfg user\\**\*                                      |
|                                     Assign LU(s) or LU pool(s) to users                                      |                                        **snacfg user**                                        |
  
 \* It is recommended that you use the SNA Manager, not the command-line interface, for these tasks. Any errors in the typing of commands for these tasks can result in a nonfunctioning configuration.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)