---
description: "Learn more about: Client Logons and the Storing of Passwords"
title: "Client Logons and the Storing of Passwords1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Client Logons and the Storing of Passwords
For security reasons, a user at a client computer may have to log on several times before obtaining access through [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] to an IBM mainframe (z/OS) midrange (IBM System i) server. Users may not always find this to be convenient. The logons are necessary because starting an SNA session requires several kinds of access: access to the Windows domain, access to a Host Integration Server computer, access to the mainframe or midrange server and, possibly, access to programs on the mainframe or IBM System i. An example of such a program is an midrange RPG for IBM System i program that uses conversation security when communicating with 5250 emulators. Each layer of access may require an additional logon depending on the operating system and the client/server protocol used on the client.  
  
 The Enterprise Single Sign-On feature of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] can reduce or even eliminate these multiple logons on Windows-based networks. If you are not able to take advantage of this feature, users can avoid multiple logons by following the procedures outlined in the following sections.  
  
 For more information, see Enterprise Single Sign-On.  
  
## See Also  
 [Types of Client Logons](../core/types-of-client-logons1.md)   
 [Overview of Network Protocols for Clients](../core/overview-of-network-protocols-for-clients2.md)
