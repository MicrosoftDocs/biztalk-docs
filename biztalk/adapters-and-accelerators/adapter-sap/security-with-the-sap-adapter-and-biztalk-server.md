---
title: "Security with the SAP adapter and BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "credentials, protecting"
  - "Enterprise Single Sign-On"
  - "security, when using BizTalk Server"
  - "security, protecting credentials"
  - "SSO"
ms.assetid: 702cd0f9-d8e1-4dad-8774-b552481d5390
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Security with the SAP adapter and BizTalk Server
When you configure a send port or a receive port (location) by using the BizTalk Server Administration console or use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas for a BizTalk solution, you must provide credentials for the SAP system. It is important to supply these credentials in a secure way to help prevent them from being revealed to potentially malicious actors. This topic discusses how to most securely supply credentials for the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] for BizTalk Server solutions.  
  
 A more general discussion of security in the context of BizTalk solutions is an expansive topic and is beyond the scope of this documentation. For information about how you can make your BizTalk solutions more secure, see the [Secure and protect your BizTalk messages](../../core/secure-and-protect-your-biztalk-messages.md).  
  
## How Do I Protect Credentials When I Use the Consume Adapter Service BizTalk Project Add-in?  
 When you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to retrieve message schemas for a BizTalk solution, you must supply a user name and password for the SAP system. You should only do this from the **Security** tab on the **Configure Adapter** dialog box. This ensures that your credentials will not be displayed in the **Uri** field of the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dialog box, where anyone with access to your computer screen can read them. For more information about how to retrieve message schemas by using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], including how to enter a user name and password for the SAP system, see [Get Metadata for SAP Operations in Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md).  
  
## How Do I Protect Credentials When I Configure a Send Port or a Receive Location?  
 BizTalk solutions use the Microsoft BizTalk WCF-Custom adapter to consume WCF services. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF custom binding that enables clients to consume the SAP system as if it were a WCF service. BizTalk solutions consume the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] through send ports and receive locations that are configured to use the WCF-Custom adapter, which is, in turn, configured to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as its transport. For more information about how to configure send ports and receive ports (receive locations), including how to configure the WCF-Custom adapter, see [Manually configure a physical port binding to the SAP adapter](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md).  
  
 You configure the SAP system credentials from the **Credentials** tab of the **WCF-Custom Transport Properties** dialog box for send ports or from the **Other** tab of the **WCF-Custom Transport Properties** dialog box for receive locations. Because the WCF-Custom adapter supports Enterprise Single Sign-On (SSO), you can choose to provide either a user name and password or an SSO affiliate application on either of these tabs. The following topics discuss both options.  
  
### User Name Password Credentials  
 You should only supply a user name and password from the **Credentials** tab (for send ports) or the **Other** tab (for receive locations) in the **WCF-Custom Transport Properties** dialog box. This ensures the following:  
  
-   Your credentials will not be displayed in the **Uri** field of the dialog box. This prevents those who have access to your screen (or who have permissions that enable them to view the send port or receive location properties) from seeing your credentials.  
  
-   Your password will not be written to the binding file if you export the send port or receive port binding. This prevents anyone from with access to the file from viewing your password.  
  
### Enterprise Single Sign-On and SSO Affiliate Applications  
 You can configure the WCF-Custom adapter to use SSO to get the credentials for the SAP system. SSO uses a database and a master secret to encrypt and store user credentials. It also provides services to map Microsoft Windows accounts to secondary credentials that are used to access a backend system. By using SSO, you can map a Windows account to a user name and password on the SAP system.  
  
 SSO uses *affiliate applications* and *SSO mappings* to map credentials to the backend system. An affiliate application is a logical entity in SSO that refers to a system or an application that requires secondary credentials. An SSO mapping is associated with an affiliate application. It maps a Windows account to the secondary credentials used by that account to access the affiliate system or application. An SSO mapping can be associated with a Windows user account or with a group.  
  
 To use SSO with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must do the following.  
  
1.  Create an affiliate application in SSO to hold the user name password credentials for the SAP system. This step is often performed by someone with special types of SSO administrative privileges.  
  
2.  Create a user or group mapping for the affiliate application that maps your Windows account to the user name and password that are used to establish a connection with the SAP system. Depending on your installation, a user might be able to perform this step or it might require someone with special types of SSO administrative privileges.  
  
> [!NOTE]
>  When configured for SSO, the WCF-Custom adapter uses services provided by SSO to get the SAP user name and password from the SSO database. It provides these (unencrypted) to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], so that the adapter can open a connection to the SAP system. SSO provides no encryption or protection across the connection between the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] and the SAP system.  
  
 For information about how to use SSO, including information about how to create affiliate applications and SSO mappings, see [Using SSO](../../core/using-sso.md). For more general information about SSO, see [Implementing Enterprise Single Sign-On](../../core/implementing-enterprise-single-sign-on.md).  
  
## The AcceptCredentialsInUri Binding Property  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces the **AcceptCredentialsInUri** binding property. This property determines whether SAP system credentials are permitted in the connection URI. By default, **AcceptCredentialsInUri** is **false** and the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] throws an exception if credentials are included in the URI.  
  
 This property is surfaced because there are certain programming scenarios that require the credentials to be present in the connection URI. This should never be the case when you are configuring a send port or a receive location, or when you are using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to retrieve message schemas from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. In such cases, it is recommended that you do not set **AcceptCredentialsInUri** to **true**. For more information about the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding properties, see [Read about the BizTalk Adapter for ORacle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
 The **AcceptCredentialsInUri** binding property is not available in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] in the **Binding** tab while configuring a WCF-Custom or WCF-SAP receive or send port. To set the value of the **AcceptCredentialsInUri** binding property, you must open the adapter bindings file (XML file) that is created after you have generated metadata using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], and then locate this binding property in the file. Specify an appropriate value for this binding property, save the binding file, and then import the binding file in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. See [Reuse SAP adapter bindings](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md) for instructions.  
  
## See Also  
[Best practices to secure the SAP adapter](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)  
 [Secure your SAP applications](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)   