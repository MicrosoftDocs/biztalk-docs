---
title: "HTTP Adapter Security Recommendations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, HTTP adapters"
  - "configuring [HTTP adapters], security"
  - "HTTP adapters, security"
ms.assetid: ef6043c2-c62a-40e5-b2e1-53e60f87a761
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Adapter Security Recommendations
You use the HTTP adapter to exchange information between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and an application by means of the Hypertext Transfer Protocol (HTTP). Applications can send messages to a server by sending HTTP POST or HTTP GET requests to a specified HTTP URL. For more information about the HTTP adapter, see [HTTP Adapter](../core/http-adapter.md). It is recommended that you use the following guidelines for securing and deploying the HTTP adapter in your environment:  
  
- Ensure you configure the Internet Information Services (IIS) settings for the HTTP adapter. For more information, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).  
  
- If you use 7.0, ensure you follow the IIS 7.0 recommendations for configuring application isolation.  
  
- When you use Basic Authentication, or when you do not use encryption at the message level, it is recommended to use Secure Sockets Layer (SSL) for both receiving and sending messages to ensure that an unauthorized person cannot sniff the user credentials.  
  
- It is recommended to use Windows integrated authentication for both sending and receiving messages.  
  
- It is recommended that you do not rename, copy, or move the ISAPI extension file. This ensures that the security update installers can correctly apply any potential security updates pertinent to this file.  
  
- You should use strong discretionary access control lists (DACLs) for the directory containing the ISAPI extension file and for the virtual directory that you create for receiving messages. Members of the BizTalk Isolated Host group for the host running the HTTP adapter need read and execute permissions, and the users that the HTTP adapter authenticates need read permissions on these directories.  
  
- When you use SSL client certificates with the HTTP send adapter, you must manually configure these certificates.  
  
- Just like other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components, it is recommended you do not put the HTTP adapter in the perimeter network. If you do, you have to open ports from the perimeter network to the data domain for SQL Server traffic to the MessageBox database, which is risk-prone. It is recommended you configure the HTTP adapter in the processing domain (that is, not the perimeter network). You can then configure the outmost firewall (FW4) to forward HTTP requests through the firewall in the processing domain (FW3). In this case, you do not need IIS in the perimeter network. This mechanism is called reverse proxy. (The Forefront Threat Management Gateway (TMG) 2010 server implementation is called Web Publishing.)  
  
- When you create an application pool for an HTTP receive location, you must configure it to run under an account that is a member of the Windows group for the isolated host running the HTTP receive adapter and the Internet Information Services Worker Process group (IIS_WPG group). You must then use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure the host instance for the HTTP receive adapter to use this account. If you change the account for the IIS_WPG group, you must ensure you also update the host instance to run under the new account. For more information, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).  
  
## See Also  
 [Ports for the Receive and Send Servers](../core/ports-for-the-receive-and-send-servers.md)   
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)