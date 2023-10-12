---
description: "Learn more about: SMTP Adapter Security Recommendations"
title: "SMTP Adapter Security Recommendations"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SMTP Adapter Security Recommendations
You use the SMTP adapter to exchange information between a server running BizTalk Server and other applications by means of the Simple Mail Transfer Protocol (SMTP) protocol. BizTalk Server can send messages to other applications by creating an e-mail message and delivering it to a specified e-mail address. You can use the SMTP adapter only for sending messages. For more information about the SMTP adapter, see [SMTP Adapter](../core/smtp-adapter.md).  
  
 When you configure the service account for the host instance running the SMTP adapter, you need to specify the type of authentication you want to use with the remote SMTP server. The authentication options are basic authentication (clear text), NTLM (by using current credentials), or none if authentication is not required by the SMTP server.  
  
 When you send a message by using the SMTP adapter, BizTalk Server sends the message in clear text by default. If you use a pipeline that has an S/MIME encoder component, you can encrypt the message before you send it to the SMTP server. However, the SMTP header is still in clear text.  
  
 If you want to audit the e-mail messages that BizTalk Server sends, you should use the SMTP adapter to connect to your own SMTP server, where you can then audit the messages.  
  
 The SMTP adapter does not support Secure Sockets Layer (SSL).  
  
## See Also  
 [Ports for the Receive and Send Servers](../core/ports-for-the-receive-and-send-servers.md)   
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)
