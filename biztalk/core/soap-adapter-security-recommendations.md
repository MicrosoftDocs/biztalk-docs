---
title: "SOAP Adapter Security Recommendations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SOAP adapters, security"
  - "security, SOAP adapters"
ms.assetid: f869bd82-df93-45e1-b747-b538820253fb
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SOAP Adapter Security Recommendations
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the SOAP adapter to publish (receive) and consume (send) Web services. For more information about the SOAP adapter, see [SOAP Adapter](../core/soap-adapter.md). For more information about Web services, see [Using Web Services](../core/using-web-services.md). It is recommended you follow these guidelines for securing and deploying the SOAP adapter in your environment.  
  
- For security recommendations for publishing Web services, see [Enabling Web Services](../core/enabling-web-services.md).  
  
- The SOAP adapter leverages the Hypertext Transfer Protocol (HTTP) to send and receive messages to and from BizTalk Server. Therefore, you must follow the security recommendations for securing Internet Information Services (IIS). If you use IIS 7.0, ensure you follow the IIS 7.0 recommendations for configuring application isolation. For more information, see [Create an Application Pool (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=196674).  
  
- When you create an application pool for a SOAP receive location, you must configure it to run under an account that is a member of the Windows group for the isolated host running the SOAP receive adapter and the Internet Information Services Worker Process group (IIS_WPG group). You must then configure the host instance for the SOAP receive adapter to use this account. If you change the account for the IIS_WPG group, you must ensure you also update the host instance to run under the new account.  
  
- When you use Secure Sockets Layer (SSL) client certificates with the SOAP send adapter, you must manually configure these certificates.  
  
- When consuming Web services, you can use anonymous, basic, digest, Windows integrated, or client certificates for authentication. When consuming Web services by using basic authentication, it is recommended to use SSL to ensure that an unauthorized person cannot read the user credentials from the message.  
  
- You can use Enterprise Single Sign-On (SSO) in scenarios where you need to map the content of the front-end user to credentials in a back-end system. For more information, see [How to Map Single Sign-On Credentials](../core/how-to-map-single-sign-on-credentials.md).  
  
- When using basic authentication, or when you do not use encryption at the message level, it is recommended to use SSL for both receiving and sending messages to ensure that an unauthorized person cannot read the user credentials.  
  
- It is recommended to use Windows integrated authentication for both sending and receiving messages.  
  
- The computer running the SOAP adapter also has the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime. It is recommended you do not put the SOAP adapter in the perimeter network. If you do, you have to open ports from the perimeter network to the data domain for SQL Server traffic to the MessageBox database, and you are exposing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime to potential attacks. It is recommended you configure the SOAP adapter in the processing domain (that is, not the perimeter network). You can then configure the outermost firewall to forward SOAP requests through the firewall in the processing domain. This mechanism is called reverse proxy. (The Forefront Threat Management Gateway (TMG) 2010 server implementation is called Web Publishing.)  
  
## See Also  
 [Ports for the Receive and Send Servers](../core/ports-for-the-receive-and-send-servers.md)   
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)