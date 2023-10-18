---
description: "Learn more about: Important Network Options on a Host Integration Server Computer"
title: "Important Network Options on a Host Integration Server Computer2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Important Network Options on a Host Integration Server Computer
When [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] network options are specified correctly on a [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer, the server will use the appropriate protocol(s) for communicating with clients. Servers supporting TCP/IP or Microsoft Networking will have the correct domain name so that clients can locate the Host Integration Server computers.  
  
> [!IMPORTANT]
>  These changes do not take effect until the server is restarted. Do not change these settings while the server has active users.  
  
### To view or change client/server protocols and other network options on a Host Integration Server computer  
  
1.  In SNA Manager, select a Host Integration Server computer.  
  
2.  Right-click a server and then click **Properties**. The **Server Properties** dialog box appears.  
  
3.  To change the Host Integration Server computer name, click **Change** in the **Name** box. The Host Integration Server computer must be in an off-line state before you can change the name.  
  
4.  To modify the client/server protocols and other network options, click **Change** in the **Properties** box, and then click **OK**.  
  
5.  Complete the Server SNA Resource wizard.  
  
> [!NOTE]
>  If the server has TCP/IP installed and will communicate with clients that use TCP/IP, be sure that the selections in the Select Client/Server Protocols dialog box include TCP/IP. If Microsoft Networking (Named Pipes) is selected and TCP/IP is not, the server can communicate through Named Pipes over TCP/IP, a protocol combination that does not recover from error conditions as effectively as native TCP/IP.  
  
 If TCP/IP is selected, you can also select Microsoft Networking. In this situation, the Host Integration Server computer will use native TCP/IP with clients that use TCP/IP, and Microsoft Networking with clients that use Microsoft Networking.  
  
## See Also  
 [Important Host Integration Server Network Options](../core/important-host-integration-server-network-options1.md)
