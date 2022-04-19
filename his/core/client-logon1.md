---
description: "Learn more about: Client Logon"
title: "Client Logon1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df6b0f0e-5452-4e2e-872e-44435b60d140
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Client Logon
The logon process conducted by a user on a client system performs the essential task of identifying the user to the Windows domain and to Host Integration Server computers in the domain. The way that Host Integration Server handles the logon process depends on the network software on the client system.  
  
 For any type of client computer, once the clients logon process for one Host Integration Server computer has been completed, additional servers can provide services without another interactive user logon. Servers can repeat the logon verification without the user being involved.  
  
 If you maintain tight security with the logon to a mainframe, it may make sense to keep access open-ended on the Host Integration Server computer.  
  
## See Also  
 [Understanding Windows Security](../core/understanding-windows-security1.md)
