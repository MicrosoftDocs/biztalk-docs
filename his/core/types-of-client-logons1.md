---
title: "Types of Client Logons1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbad90fa-d163-4459-a86d-4b5fbc630404
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Types of Client Logons
The number of logons required for establishing an SNA session from a client varies, depending mostly on what client/server protocol the client computer is using. The following list describes the logons:  
  
## Clients Using Microsoft Networking  
 A client using Microsoft Networking must log on to the Windows domain and then must perform any logons required on the mainframe or AS/400. For example, a client using Microsoft Networking and also using a 5250 emulator would log on once to the Windows domain, once to the AS/400 itself, and (in many cases) once to the AS/400 program that communicates with the 5250 emulator.  
  
 After clients using Microsoft Networking are logged on to the domain, no additional logon is needed for access to [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computers in the domain. That is, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] can securely confirm the domain logon without any additional action by the user.  
  
## Clients Using TCP/IP  
 A client using TCP/IP must log on to the Host Integration Server computers even if the client has already accessed other resources in the Windows domain, and then must perform any logons required on the mainframe or AS/400.  
  
## See Also  
 [Overview of Network Protocols for Clients](../core/overview-of-network-protocols-for-clients2.md)