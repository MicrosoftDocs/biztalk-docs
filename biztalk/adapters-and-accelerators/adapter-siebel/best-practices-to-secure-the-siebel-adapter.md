---
title: "Best practices to secure the Siebel adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security best practices, for consuming the Siebel adapter with BizTalk Server"
  - "security best practices, for connection between the Siebel adapter and Siebel system"
  - "best practices, security"
  - "security, best practices"
  - "security best practices, for hosting the Siebel adapter in IIS"
  - "security best practices, for WCF diagnostic tracing and message logging"
  - "security best practices, for consuming the Siebel adapter with programming solutions"
ms.assetid: da89fcc5-2705-4198-8df6-64b2c532ef41
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best practices to secure the Siebel adapter
This section provides best practices that you should follow to more completely protect sensitive data when you use or develop applications that consume the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].  
  
## Security Best Practices for the Connection between the Siebel Adapter and the Siebel System  
  
- The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] supports mscrypto or rsa encryption on the data exchanged between the adapter and the Siebel system. To help ensure the privacy of the data that is exchanged between the adapter and the Siebel system, you should enable one of these encryption modes.  
  
- The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] does not provide mechanisms to help ensure data integrity or to provide for authentication and authorization on the data that is exchanged between it and the Siebel system. You must provide such mechanisms, if these concerns exist in your environment.  
  
- Do not provide user name password credentials for the Siebel system in the connection URI. See the remainder of this topic for alternative methods of providing credentials to the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
  For more information, see [Security between Siebel and the adapter](../../adapters-and-accelerators/adapter-siebel/security-between-the-siebel-system-and-the-adapter.md)
  
## Security Best Practices for Consuming the Siebel Adapter with BizTalk Server  
  
- Do not provide user name password credentials for the Siebel system in the connection URI.  
  
- When you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], enter the user name password credentials for the Siebel system from the **Security** tab of the **Configure Adapter** dialog box.  
  
- When you configure the BizTalk WCF-Custom adapter for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] on a send port, enter the user name password credentials for the Siebel system from the **Credentials** tab of the **Configure WCF Custom Transport** dialog box.  
  
- When you configure the BizTalk WCF-Custom adapter for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] on a receive location, enter the user name password credentials for the Siebel system from the **Other** tab of the **Configure WCF Custom Transport** dialog box.  
  
  For more information, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)
  
## Security Best Practices for Consuming the Siebel Adapter with Programming Solutions  
  
- It is sometimes necessary to provide the user name password credentials for the Siebel system in the connection URI; however, if possible, you should avoid doing this.  
  
- When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], enter the user name password credentials for the Siebel system from the **Security** tab of the **Configure Adapter** dialog box.  
  
- In WCF Channel Model programming, use the **Credentials** property on the channel factory to set the user name password credentials for the Siebel system.  
  
- In WCF Service Model programming, use the **ClientCredentials** property on the WCF client to set the user name password credentials for the Siebel system.  
  
- If an application that consumes the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] sends messages that contain sensitive database information across a process boundary to another service or client, ensure that these messages have sufficient security measures applied to provide adequate data protection in your environment.  
  
  For more information see, [Secure programming with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/secure-programming-with-the-siebel-adapter.md) 
  
## Security Best Practices for Hosting the Siebel Adapter in IIS  
  
- Hosting the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in Microsoft Internet Information Services (IIS) as a Web service exposes operations surfaced by the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to Web clients. These operations might involve exchanging sensitive data over the Internet, so you should take measures to help ensure that this data is as secure as possible.  
  
   [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides two standard bindings for HTTP transport: the **BasicHttpBinding** provides basic HTTP transport with no security mechanisms; the **WSHttpBinding** supports both transport-level and message-level security mechanisms.  
  
   You can either use the **BasicHttpBinding** over an HTTPS connection, or use the **WSHttpBinding** to help protect your data. The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] includes the [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)] to generate WCF services for LOB artifacts. This wizard only supports use of **BasicHttpBinding**.  
  
   You can also develop a custom HTTP binding to leverage additional security mechanisms that your environment provides. For more information about the security features that [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides, see [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx).
  
## Security Best Practices for WCF Diagnostic Tracing and Message Logging  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] supports diagnostic tracing and message logging. You configure diagnostic tracing and message logging either through configuration files or by using Windows Management Instrumentation (WMI). Depending on the configuration options you set, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] diagnostic tracing or message logging can emit sensitive information to log files, where it could potentially be exposed to observation by unauthorized users.  
  
 Follow the recommendations provided in the WCF documentation to mitigate potential security threats exposed by enabling these features. At a minimum, you should observe the following best practices for diagnostic tracing and message logging:  
  
- Do not enable “verbose” or “information” tracing in a production environment. This may lead to performance degradation. However, you must enable “warning” and “error” tracing in a production environment. If you enable tracing, you must take proper security measures to protect your data. See the WCF documentation for more information.  
  
- Ensure that log files and configuration files are protected by access control lists (ACLs).  
  
  The following warnings apply specifically to the messages that are exchanged between a client application and the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]:  
  
- [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] diagnostic tracing can log the header (but not the body) of messages exchanged with the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Because the message action is in the message header, this reveals the operations invoked on the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] by the client.  
  
- If [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] message logging is enabled and `logMessagesAtServiceLevel` is `true`, the message header (but not the message body) of messages exchanged between the adapter client and the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] are logged. Because the message action is in the message header, this reveals the operations that the client invoked on the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. If `logEntireMessage` is also `true`, the message body will be logged. This can reveal sensitive database information.  
  
  For more information about improving security when you enable diagnostic tracing, see [Security Concerns and Useful Tips for Tracing](https://msdn.microsoft.com/library/ms733053.aspx). For more information about improving security when you enable message logging, see [Security Concerns for Message Logging](https://msdn.microsoft.com/library/ms730318.aspx).
  
## See Also  
[Secure your Siebel applications](../../adapters-and-accelerators/adapter-siebel/secure-your-siebel-applications.md)