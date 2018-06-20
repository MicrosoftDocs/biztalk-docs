---
title: "Best practices to secure the Oracle Database adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, best practices for connection between the Oracle Database adapter and the Oracle database"
  - "security, best practices for WCF diagnostic tracing and message logging"
  - "security, best practices for hosting the Oracle Database adapter in IIS"
  - "credentials"
  - "security, best practices"
  - "security"
  - "security, best practices for consuming the Oracle Database adapter with BizTalk Server"
  - "security, protecting sensitive data"
  - "user name password credential"
  - "security, best practices for consuming the Oracle Database adapter with programming solutions"
ms.assetid: 689e8442-91c9-4fe0-a0a0-ce5f5a98ab38
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best practices to secure the Oracle Database adapter
This section provides best practices that you should follow to more completely protect sensitive data when you use or develop applications that consume the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].  
  
## Security Best Practices for the Connection between the Oracle Database Adapter and the Oracle Database  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] provides no support for helping to secure communication between it and the Oracle database. You must provide a mechanism to help ensure an adequate level of security for data exchanged between the adapter and the Oracle database.  
  
- Do not provide user name password credentials for the Oracle database in the connection URI. See the following sections for alternative methods of providing credentials to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] also enables you to use Windows Authentication while connecting to the Oracle database to generate metadata and perform operations, either through [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Before using Windows Authentication, you must perform the steps listed in [Connecting to the Oracle Database Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md).  
  
  For more information, see [Security between the Oracle Database and the adapter](../../adapters-and-accelerators/adapter-oracle-database/security-between-the-oracle-database-and-the-adapter.md).  
  
## Security Best Practices for Consuming the Oracle Database Adapter with BizTalk Server  
  
- Do not provide user name password credentials for the Oracle database in the connection URI.  
  
- When you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], enter the user name password credential for the Oracle database from the **Security** tab of the **Configure Adapter** dialog box.  
  
- When you configure the BizTalk WCF-Custom adapter for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] on a send port, enter the user name password credential for the Oracle database from the **Credentials** tab of the **Configure WCF Custom Transport** dialog box.  
  
- When you configure the BizTalk WCF-Custom adapter for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] on a receive location, enter the user name password credential for the Oracle database from the **Other** tab of the **Configure WCF Custom Transport** dialog box.  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] also enables you to use Windows Authentication while connecting to the Oracle database to generate metadata and perform operations through [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Before using Windows Authentication, you must perform the steps listed in [Connecting to the Oracle Database Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md).  
  
  For more information, see [Security with the Oracle Database adapter and BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md).
  
## Security Best Practices for Consuming the Oracle Database Adapter with Programming Solutions  
  
- It is sometimes necessary to provide the user name password credentials for the Oracle database in the connection URI; however, if possible, you should avoid doing this.  
  
- When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], enter the user name password credential for the Oracle database from the **Security** tab of the **Configure Adapter** dialog box.  
  
- In WCF Channel Model programming, use the **Credentials** property on the channel factory to set the user name password credential for the Oracle database.  
  
- In WCF Service Model programming, use the **ClientCredentials** property on the WCF client to set the user name password credential for the Oracle database.  
  
- If an application that consumes the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] sends messages that contain sensitive database information across a process boundary to another service or client, ensure that these messages have sufficient security measures applied to provide adequate data protection in your environment.  
  
- The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] also enables you to use Windows Authentication while connecting to the Oracle database to generate metadata and perform operations through [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Before using Windows Authentication, you must perform the steps listed in [Connecting to the Oracle Database Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md).  
  
  For more information see, [Secure programming with the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/secure-programming-with-the-oracle-database-adapter.md).  
  
## Security Best Practices for Hosting the Oracle Database Adapter in IIS  
 Hosting the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in Microsoft Internet Information Services (IIS) as a Web service exposes operations surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to Web clients. These operations might involve exchanging sensitive data over the Internet, so you should take measures to help ensure that this data is as secure as possible.  
  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides two standard bindings for HTTP transport: the **BasicHttpBinding** provides basic HTTP transport with no security mechanisms; the **WSHttpBinding** supports both transport-level and message-level security mechanisms.  
  
 You can either use the **BasicHttpBinding** over an HTTPS connection, or use the **WSHttpBinding** to help protect your data. The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] includes the [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)] to generate WCF service for LOB artifacts. This wizard only supports use of **BasicHttpBinding**.  
  
 You can also develop a custom HTTP binding to leverage additional security mechanisms that your environment provides. For more information about the security features that [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides, see [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx).  
  
## Security Best Practices for WCF Diagnostic Tracing and Message Logging  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] supports diagnostic tracing and message logging. You configure diagnostic tracing and message logging either through configuration files or by using Windows Management Instrumentation (WMI). Depending on the configuration options you set, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] diagnostic tracing or message logging can emit sensitive information to log files, where it could potentially be exposed to observation by unauthorized users.  
  
 Follow the recommendations provided in the WCF documentation to mitigate potential security threats exposed by enabling these features. At a minimum, you should observe the following best practices for diagnostic tracing and message logging:  
  
- Do not enable “verbose” or “information” tracing in a production environment. This may lead to performance degradation. However, you must enable “warning” and “error” tracing in a production environment. If you enable tracing, you must take proper security measures to protect your data. See the WCF documentation for more information.  
  
- Ensure that log files and configuration files are protected by access control lists (ACLs).  
  
  The following warnings apply specifically to the messages that are exchanged between a client application and the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:  
  
- [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] diagnostic tracing can log the header (but not the body) of messages exchanged with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Because the message action is in the message header, this reveals the operations invoked on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by the client.  
  
- If [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] message logging is enabled and `logMessagesAtServiceLevel` is `true`, the message header (but not the message body) of messages exchanged between the adapter client and the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] are logged. Because the message action is in the message header, this reveals the operations that the client invoked on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. If `logEntireMessage` is also `true`, the message body will be logged. This can reveal sensitive database information.  
  
  For more information about improving security when you enable diagnostic tracing, see [Security Concerns and Useful Tips for Tracing](https://msdn.microsoft.com/library/ms733053.aspx). For more information about improving security when you enable message logging, see [Security Concerns for Message Logging](https://msdn.microsoft.com/library/ms730318.aspx). 
  
## See Also  
[Secure your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)