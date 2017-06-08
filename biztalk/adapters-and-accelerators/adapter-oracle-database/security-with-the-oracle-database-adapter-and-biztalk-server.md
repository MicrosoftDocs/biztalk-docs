---
title: "Security with the Oracle Database adapter and BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "user name password credentials"
  - "SSO mapping"
  - "credentials"
  - "credentials, protecting"
  - "credentials, security considerations"
  - "affiliate application"
ms.assetid: c7e0be64-4ab9-4ee3-b88a-4f8f5f07b280
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Security with the Oracle Database adapter and BizTalk Server
When you configure a send port or a receive port (location) by using the BizTalk Server Administration console or use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas for a BizTalk solution, you must provide credentials for the Oracle database. It is important to supply these credentials in a secure way to help prevent them from being revealed to potentially malicious actors. This topic discusses how to most securely supply credentials for the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] for BizTalk Server solutions.  
  
 A more general discussion of security in the context of BizTalk solutions is an expansive topic and is beyond the scope of this documentation. For information about how you can make your BizTalk solutions more secure, see [Secure and protect your BizTalk messages](../../core/secure-and-protect-your-biztalk-messages.md).  
  
## How Do I Protect Credentials When I Use the Consume Adapter Service BizTalk Project Add-in or Add Adapter Metadata Wizard?  
 When you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to retrieve message schemas for a BizTalk solution, you must supply a user name and password for the Oracle database. You should only do this from the **Security** tab on the **Configure Adapter** dialog box. This ensures that your credentials will not be displayed in the **Configure a URI** field of the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dialog box, where anyone with access to your computer screen can read them. For more information about how to retrieve message schemas by using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], including how to enter a user name and password for the Oracle database, see [Get metadata for Oracle operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md).  
  
## How Do I Protect Credentials When I Configure a Send Port or a Receive Location?  
 BizTalk solutions use the Microsoft BizTalk WCF-Custom adapter to consume WCF services. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF custom binding that enables clients to consume the Oracle database as if it were a WCF service. BizTalk solutions consume the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] through send ports and receive locations that are configured to use the WCF-Custom adapter, which is, in turn, configured to use the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] as its transport. For more information about how to configure send ports and receive ports (receive locations), including how to configure the WCF-Custom adapter, see [Manually configure a physical port binding to the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md).  
  
 You configure the Oracle database credentials from the **Credentials** tab of the **WCF-Custom Transport Properties** dialog box for send ports or from the **Other** tab of the **WCF-Custom Transport Properties** dialog box for receive locations. Because the WCF-Custom adapter supports Enterprise Single Sign-On (SSO), you can choose to provide either a user name and password or an SSO affiliate application on either of these tabs. The following topics discuss both options.  
  
### User Name Password Credentials  
 You should only supply a user name and password from the **Credentials** tab (for send ports) or the **Other** tab (for receive locations) in the **WCF-Custom Transport Properties** dialog box. This ensures the following:  
  
-   Your credentials will not be displayed in the **Address (URI)** field of the dialog box. This prevents those who have access to your screen (or who have permissions that enable them to view the send port or receive location properties) from seeing your credentials.  
  
-   Your password will not be written to the binding file if you export the send port or receive port binding. This prevents anyone from with access to the file from viewing your password.  
  
### Enterprise Single Sign-On and SSO Affiliate Applications  
 You can configure the WCF-Custom adapter to use Enterprise Single Sign-on (SSO) to get the credentials for the Oracle database. SSO uses a database and a master secret to encrypt and store user credentials. It also provides services to map Microsoft Windows accounts to secondary credentials that are used to access a back-end system. By using SSO, you can map a Windows account to a user name and password on the Oracle database.  
  
 SSO uses *affiliate applications* and *SSO mappings* to map credentials to the back-end system. An affiliate application is a logical entity in SSO that refers to a system or an application that requires secondary credentials. An SSO mapping is associated with an affiliate application. It maps a Windows account to the secondary credentials used by that account to access the affiliate system or application. An SSO mapping can be associated with a Windows user account or with a group.  
  
 To use SSO with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must do the following.  
  
1.  Create an affiliate application in SSO to hold the user name password credentials for the Oracle database. This step is often performed by someone with special types of SSO administrative privileges.  
  
2.  Create a user or group mapping for the affiliate application that maps your Windows account to the user name and password that are used to establish a connection with the Oracle database. Depending on your installation, a user might be able to perform this step or it might require someone with special types of SSO administrative privileges.  
  
> [!NOTE]
>  When configured for SSO, the WCF-Custom adapter uses services provided by SSO to get the Oracle user name and password from the SSO database. It provides these (unencrypted) to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], so that the adapter can open a connection to the Oracle database. SSO provides no encryption or protection across the connection between the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] and the Oracle database.  
  
 For information about how to use SSO, including information about how to create affiliate applications and SSO mappings, see [Using SSO](../../core/using-sso.md). For more general information about SSO, see [Implementing Enterprise Single Sign-On](../../core/implementing-enterprise-single-sign-on.md).  
  
## The AcceptCredentialsInUri Binding Property  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces the **AcceptCredentialsInUri** binding property. This property determines whether Oracle database credentials are permitted in the connection URI. By default, **AcceptCredentialsInUri** is **false** and the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] throws an exception if credentials are included in the URI.  
  
 This property is surfaced because there are certain programming scenarios that require the credentials to be present in the connection URI. This should never be the case when you are configuring a send port or a receive location, or when you are using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to retrieve message schemas from the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. It is recommended that you do not set **AcceptCredentialsInUri** to **true**. For more information about the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
 The **AcceptCredentialsInUri** binding property is not available in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] in the **Binding** tab while configuring a WCF-Custom or WCF-OracleDB receive or send port. To set the value of the **AcceptCredentialsInUri** binding property, you must open the adapter bindings file (XML file) that is created after you have generated metadata using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], and then locate this binding property in the file. Specify an appropriate value for this binding property, save the binding file, and then import the binding file in BizTalk Server. See [Reuse SQL adapter bindings](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).  
  
## See Also  
 [Secure your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)   
[Best Practices](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)