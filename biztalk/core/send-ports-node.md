---
title: "Send Ports Node | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.node.sendports"
ms.assetid: 8fd747c8-b69e-4a31-b201-03510f91c918
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Send Ports Node
Use the **Send Ports** node to display existing send ports, create new send ports, and refresh send port information. Right-click the **Send Ports** node to display the following commands:  
  
-   **New**. This menu item displays a submenu containing the following commands:  
  
    -   **Static One-way Send Port**. Creates a new static one-way send port and displays the **Send Port Properties** window, where you can configure the new send port. A static, one-way port is associated with a specified destination address and transport type and transmits data in only one direction.  
  
    -   **Static Solicit-Response Send Port**. Creates a new static solicit-response send port and displays the **Send Port Properties** window, where you can configure the new send port. A static port is associated with a specified destination address and transport type. A solicit-response port queries the destination for a message, waits for a response message, and then submits the response message back to the server.  
  
    -   **Dynamic One-way Send Port**. Creates a new dynamic one-way send port and displays the **Send Port Properties** window, where you can configure the new send port. A dynamic port does not specify a destination address and transport type; the destination address and transport type are associated with the port during runtime. A one-way port transmits data in one direction.  
  
    -   **Dynamic Solicit-Response Send Port**. Creates a new dynamic solicit-response send port and displays the **Send Port Properties** window, where you can configure the new send port. A dynamic solicit-response send port both specifies the destination address and transport type at runtime and queries the destination for a message before submitting a response.  
  
## See Also  
 [How to Enlist a Send Port or Send Port Group](../core/how-to-enlist-a-send-port-or-send-port-group.md)   
 [Managing Send Ports and Send Port Groups](../core/managing-send-ports-and-send-port-groups.md)   
 [How to Start a Send Port or Send Port Group](../core/how-to-start-a-send-port-or-send-port-group.md)   
 [How to Stop a Send Port or Send Port Group](../core/how-to-stop-a-send-port-or-send-port-group.md)   
 [How to Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md)   
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)