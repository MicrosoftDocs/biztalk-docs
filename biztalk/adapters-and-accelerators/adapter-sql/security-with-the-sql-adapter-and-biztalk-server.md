---
description: "Learn more about: Security with the SQL adapter and BizTalk Server"
title: "Security with the SQL adapter and BizTalk Server"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Security with the SQL adapter and BizTalk Server
When you configure a send port or a receive port (location) by using the BizTalk Server Administration console or use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas for a BizTalk solution, you must provide credentials for the SQL Server database. It is important to supply these credentials in a secure way to help prevent them from being revealed to potentially malicious actors. This topic discusses how to most securely supply credentials for the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] for BizTalk Server solutions.  
  
 A more general discussion of security in the context of BizTalk solutions is an expansive topic and is beyond the scope of this documentation. For information about how you can make your BizTalk solutions more secure, see [Secure and protect your BizTalk messages](../../core/secure-and-protect-your-biztalk-messages.md).
  
## How Do I Protect Credentials When I Use the Consume Adapter Service BizTalk Project Add-in?  
 When you use the [!INCLUDE[consumeadapterservshort_md](../../includes/consumeadapterservshort-md.md)] to retrieve message schemas for a BizTalk solution, you must supply the user name and password from the **Security** tab on the **Configure Adapter** dialog box. The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] will not allow you to set credentials in the **Configure a URI** field. This improves security by preventing credentials from appearing in clear text. For more information about how to retrieve message schemas by using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], including how to enter a user name and password for the SQL Server database, see [Get metadata for SQL Server operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
## How Do I Protect Credentials When I Configure a Send Port or a Receive Location?  
 BizTalk solutions use the Microsoft BizTalk WCF-Custom adapter to consume WCF services. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF custom binding that enables clients to consume the SQL Server database as if it were a WCF service. BizTalk solutions consume the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] through send ports and receive locations that are configured to use the WCF-Custom adapter. The WCF-Custom adapter is, in turn, configured to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] as its transport. For more information about how to configure send ports and receive ports (receive locations), including how to configure the WCF-Custom adapter, see [Manually configure a physical port binding to the SQL adapter](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).
  
 You configure the SQL Server database credentials from the **Credentials** tab of the **WCF-Custom Transport Properties** dialog box for send ports or from the **Other** tab of the **WCF-Custom Transport Properties** dialog box for receive locations. Because the WCF-Custom adapter supports Enterprise Single Sign-On (SSO), you can also choose to provide either a user name and password or an SSO affiliate application on either of these tabs. The following topics discuss both options.  
  
### User Name Password Credentials  
 You should only supply a user name and password from the **Credentials** tab (for send ports) or the **Other** tab (for receive locations) in the **WCF-Custom Transport Properties** dialog box. This ensures the following:  
  
-   Your credentials will not be displayed in the **Address (URI)** field of the dialog box. This prevents those who have access to your screen (or who have permissions that enable them to view the send port or receive location properties) from seeing your credentials.  
  
-   Your password will not be written to the binding file if you export the send port or receive port binding. This prevents anyone with access to the file from viewing your password.  
  
### Enterprise Single Sign-On and SSO Affiliate Applications  
 You can configure the WCF-Custom adapter so that it uses Enterprise Single Sign-on (SSO) to get the credentials for the SQL Server database. SSO uses a database and a master secret to encrypt and store user credentials. It also provides services to map Microsoft Windows accounts to secondary credentials that are used to access a back-end system. By using SSO, you can map a Windows account to a user name and password on the SQL Server database.  
  
 SSO uses *affiliate applications* and *SSO mappings* to map credentials to the back-end system. An affiliate application is a logical entity in SSO that refers to a system or an application that requires secondary credentials. An SSO mapping is associated with an affiliate application. It maps a Windows account to the secondary credentials used by that account to access the affiliate system or application. An SSO mapping can be associated with a Windows user account or with a group.  
  
 To use SSO with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must do the following.  
  
1.  Create an affiliate application in SSO to hold the user name password credentials for the SQL Server database. This step is often performed by someone with special types of SSO administrative privileges.  
  
2.  Create a user or group mapping for the affiliate application that maps your Windows account to the user name and password that are used to establish a connection with the SQL Server database. Depending on your installation, a user might be able to perform this step, or it might require someone with special types of SSO administrative privileges.  
  
> [!NOTE]
>  When configured for SSO, the WCF-Custom adapter uses services provided by SSO to get the SQL Server user name and password from the SSO database. It provides these (unencrypted) to the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], so that the adapter can open a connection to the SQL Server database. SSO provides no encryption or protection across the connection between the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] and the SQL Server database.  
  
 For information about how to use SSO, including information about how to create affiliate applications and SSO mappings, see [Using SSO](../../core/using-sso.md). For more general information about SSO, see [Implementing Enterprise Single Sign-On](../../core/implementing-enterprise-single-sign-on.md).
  
## The AcceptCredentialsInUri Binding Property  
 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not support **AcceptCredentialsInUri** binding property. Credentials are never permitted in the connection URI.  
  
## See Also  
[Secure your SQL applications](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)  
[Best practices to secure the SQL adapter](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)
