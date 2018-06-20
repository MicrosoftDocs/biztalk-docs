---
title: "Best practices to secure the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e32379d7-800a-49b7-a09a-6b3f04a6e5ef
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best practices to secure the SQL adapter
Best practices that you should follow to more completely protect sensitive data when you use or develop applications that consume the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].  
  
## Security Best Practices for the Connection between the SQL Adapter and the SQL Server Database  
  
- The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] provides no support for helping to secure communication between it and the SQL Server database. You must provide a mechanism to help ensure an adequate level of security for data exchanged between the adapter and the SQL Server database.  
  
- For security reasons, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not allow you to provide user name password credentials for the SQL Server database in the connection URI. See the remainder of this topic for alternative methods of providing credentials to the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
- The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] also enables you to use Windows Authentication while connecting to SQL Server to generate metadata and perform operations, either through [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Before using Windows Authentication, you must add the Windows user as a user in SQL Server Management Studio. For more information, see [Connect to SQL Server using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
  For more information, see [Security between the SQL Server and the adapter](../../adapters-and-accelerators/adapter-sql/security-between-the-sql-server-and-the-adapter.md).
  
## Security Best Practices for Consuming the SQL Adapter with BizTalk Server  
  
- The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not allow you to provide user name password credentials for the SQL Server database in the connection URI.  
  
- When you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], enter the user name password credential for the SQL Server database from the **Security** tab of the **Configure Adapter** dialog box.  
  
- When you configure the BizTalk WCF-Custom adapter for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a send port, enter the user name password credential for the SQL Server database from the **Credentials** tab of the **WCF-Custom Transport Properties** dialog box.  
  
- When you configure the BizTalk WCF-Custom adapter for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a receive location, enter the user name password credential for the SQL Server database from the **Other** tab of the **WCF-Custom Transport Properties** dialog box.  
  
- While using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate metadata, configuring send port, or configuring receive port, you can also use Windows Authentication. Before using Windows Authentication, you must add the Windows user as a user in SQL Server Management Studio. For more information, see [Connect to SQL Server using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
  For more information, see [Security with the SQL adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md).
  
## Security Best Practices for Consuming the SQL Adapter with Programming Solutions  
  
- It is sometimes necessary to provide the user name password credentials for the SQL Server database in the connection URI; however, if possible, you should avoid doing this.  
  
- When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], enter the user name password credential for the SQL Server database from the **Security** tab of the **Configure Adapter** dialog box.  
  
- In WCF channel model programming, use the **Credentials** property on the channel factory to set the user name password credential for the SQL Server database.  
  
- In WCF service model programming, use the **ClientCredentials** property on the WCF client to set the user name password credential for the SQL Server database.  
  
- If an application that consumes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sends messages that contain sensitive database information across a process boundary to another service or client, ensure that these messages have sufficient security measures applied to provide adequate data protection in your environment.  
  
- While using [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or connecting to SQL Server from a .NET application, you can also use Windows Authentication. Before using Windows Authentication, you must add the Windows user as a user in SQL Server Management Studio. For more information, see [Connect to SQL Server using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
  For more information, see [Secure programming with the SQL adapter](../../adapters-and-accelerators/adapter-sql/secure-programming-with-the-sql-adapter.md). 
  
## Security Best Practices for Hosting the SQL Adapter in IIS  
 Hosting the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in Microsoft Internet Information Services (IIS) as a Web service exposes operations surfaced by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to Web clients. These operations might involve exchanging sensitive data over the Internet, so you should take measures to help ensure that this data is as secure as possible.  
  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides two standard bindings for HTTP transport: the **BasicHttpBinding** provides basic HTTP transport with no security mechanisms; the **WSHttpBinding** supports both transport-level and message-level security mechanisms.  
  
 You can either use the **BasicHttpBinding** over an HTTPS connection, or use the **WSHttpBinding** to help protect your data. The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] includes the [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)] to generate WCF service for LOB artifacts. This wizard only supports use of **BasicHttpBinding**.  
  
 You can also develop a custom HTTP binding to leverage additional security mechanisms that your environment provides. For more information about the security features that [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides, see [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx). 
  
 When hosting the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] as a Web service, Web developers should take measures to prevent strings typed in by users from being passed directly to the SQL Server database. For example, if a Web site lets the user enter a value that will be part of a WHERE clause in a SELECT statement, the input string should be scanned to prevent adding other commands to the statement.  
  
## Security Best Practices for WCF Diagnostic Tracing and Message Logging  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] supports diagnostic tracing and message logging. You configure diagnostic tracing and message logging either through configuration files or by using Windows Management Instrumentation (WMI). Depending on the configuration options you set, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] diagnostic tracing or message logging can emit sensitive information to log files, where it could potentially be exposed to observation by unauthorized users.  
  
 Follow the recommendations provided in the WCF documentation to mitigate potential security threats exposed by enabling these features. At a minimum, you should observe the following best practices for diagnostic tracing and message logging:  
  
- Do not enable “verbose” or “information” tracing in a production environment. This may lead to performance degradation. However, you must enable “warning” and “error” tracing in a production environment. If you enable tracing, you must take proper security measures to protect your data. See the WCF documentation for more information.  
  
- Ensure that log files and configuration files are protected by access control lists (ACLs).  
  
  The following warnings apply specifically to the messages that are exchanged between a client application and the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:  
  
- [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] diagnostic tracing can log the header (but not the body) of messages exchanged with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Because the message action is in the message header, this reveals the operations invoked on the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] by the client.  
  
- If [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] message logging is enabled and `logMessagesAtServiceLevel` is `true`, the message header (but not the message body) of messages exchanged between the adapter client and the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] are logged. Because the message action is in the message header, this reveals the operations that the client invoked on the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. If `logEntireMessage` is also `true`, the message body will be logged. This can reveal sensitive database information.  
  
  For more information about improving security when you enable diagnostic tracing, see [Security Concerns and Useful Tips for Tracing](https://msdn.microsoft.com/library/ms733053.aspx). For more information about improving security when you enable message logging, see [Security Concerns for Message Logging](https://msdn.microsoft.com/library/ms730318.aspx).
  
## See Also  
[Secure your SQL applications](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)