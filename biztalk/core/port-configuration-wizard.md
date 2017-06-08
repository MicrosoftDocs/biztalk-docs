---
title: "Port Configuration Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.port.config.wizard"
ms.assetid: 73a30b25-5983-4254-a561-bca03783a9ec
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Port Configuration Wizard
The Port Configuration Wizard enables you to configure all of the details associated with a port, including port type, pattern of communication, access restrictions, communication direction, and binding information.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Communication pattern**|Select **One-Way** to specify that messages will always move in a single direction through this port, or select **Request-Response** if the port will be used for a request-response combination.|  
|**Access restrictions**|Select the scope within which this port is accessible.|  
|**Port direction of communication**|From the drop-down list, specify that this port will send messages, receive them, or, in the case of a request-response combination, first send and then receive, or first receive and then send.|  
|**Port binding: Specify later**|Defer configuration of this port; in this case, it will be configured at deployment time.|  
|**Port binding: Specify now**|Type a URI to which the port will be bound. From the **Transport** drop-down list, select a transport type. From the available pipeline drop-down list, select a pipeline for the port.|  
|**Port binding: Direct**|Use the radio buttons to specify that this port will communicate directly with another port, will be self-correlating, or will use filter expressions to subscribe to incoming messages.|  
  
## See Also  
 [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md)