---
title: "Security with the Oracle E-Business Suite adapter and BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d4a816c-505d-4d5d-9eb9-04847f9b5861
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Security with the Oracle E-Business Suite adapter and BizTalk Server
When you configure a send port or a receive port (location) by using the BizTalk Server Administration console or use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas for a BizTalk solution, you must provide credentials for the Oracle E-Business Suite. It is important to supply these credentials in a secure way to help prevent them from being revealed to potentially malicious actors. This topic discusses how to most securely supply credentials for the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] for BizTalk Server solutions.  
  
 A more general discussion of security in the context of BizTalk solutions is an expansive topic and is beyond the scope of this documentation. For information about how you can make your BizTalk solutions more secure, see [Secure and protect your BizTalk messages](../../core/secure-and-protect-your-biztalk-messages.md).   
  
## How Do I Protect Credentials When I Use the Consume Adapter Service BizTalk Project Add-in or Add Adapter Metadata Wizard?  
 When you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to retrieve message schemas for a BizTalk solution, you can provide credentials to connect to Oracle E-Business Suite in the following two places:  
  
- On the **Security** tab in the **Configure Adapter** dialog box. This ensures that your credentials will not be displayed in the **Configure a URI** field of the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dialog box, where anyone with access to your computer screen can read them.  
  
- In the **OracleUserName** and **OraclePassword** binding properties on the **Binding Properties** tab in the **Configure Adapter** dialog box. For security reasons, the **OraclePassword** binding property is not available in the binding file (XML file) file generated as a result of using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
  > [!NOTE]
  >  Using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] does not generate any binding file.  
  
  For more information about how to retrieve message schemas by using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], see [Get metadata for Oracle E-Business Suite operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md).  
  
## How Do I Protect Credentials When I Configure a Send Port or a Receive Location?  
 BizTalk solutions use the Microsoft BizTalk WCF-Custom or WCF-Oracle EBS adapter to consume WCF services. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is a WCF binding that enables clients to consume the Oracle E-Business Suite as if it were a WCF service. BizTalk solutions consume the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] through send ports and receive locations that are configured to use the WCF-Custom or WCF-OracleEBS adapter, which is, in turn, configured to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] as its transport. For more information about how to configure send ports and receive ports (receive locations), including how to configure the WCF-Custom adapter, see [Configure a physical port binding using a port binding file to Oracle Database](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).  
  
 You configure the Oracle E-Business Suite credentials from the **Credentials** tab of the **WCF-Custom Transport Properties** dialog box for send ports or from the **Other** tab of the **WCF-Custom Transport Properties** dialog box for receive locations. Because the WCF-Custom or WCF-Oracle EBS adapter supports Enterprise Single Sign-On (SSO), you can choose to provide either a user name and password or an SSO affiliate application on either of these tabs. The following topics discuss both options.  
  
### User Name Password Credentials  
 You should only supply a user name and password from the **Credentials** tab (for send ports) or the **Other** tab (for receive locations) in the **WCF-Custom Transport Properties** dialog box. This ensures the following:  
  
-   Your credentials will not be displayed in the **Address (URI)** field of the dialog box. This prevents those who have access to your screen (or who have permissions that enable them to view the send port or receive location properties) from seeing your credentials.  
  
-   Your password will not be written to the binding file if you export the send port or receive port binding. This prevents anyone from with access to the file from viewing your password.  
  
### OraclePassword Binding Property  
 The value that you specify in the **OraclePassword** binding property for the send or receive port is available in clear text when you export bindings from an application in BizTalk Server. Therefore, after exporting a binding file from an application in  BizTalk Server, you must manually remove the value of the **OraclePassword** binding property from the binding file, and then specify it again on each host where the exported binding will be used.  
  
### Enterprise Single Sign-On and SSO Affiliate Applications  
 You can configure the WCF-Custom adapter to use Enterprise Single Sign-on (SSO) to get the credentials for the Oracle E-Business Suite. SSO uses a database and a master secret to encrypt and store user credentials. It also provides services to map Microsoft Windows accounts to secondary credentials that are used to access a back-end system. By using SSO, you can map a Windows account to a user name and password on the Oracle database.  
  
 SSO uses *affiliate applications* and *SSO mappings* to map credentials to the back-end system. An affiliate application is a logical entity in SSO that refers to a system or an application that requires secondary credentials. An SSO mapping is associated with an affiliate application. It maps a Windows account to the secondary credentials used by that account to access the affiliate system or application. An SSO mapping can be associated with a Windows user account or with a group.  
  
 To use SSO with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must do the following.  
  
1.  Create an affiliate application in SSO to hold the user name password credentials for the Oracle E-Business Suite. This step is often performed by someone with special types of SSO administrative privileges.  
  
2.  Create a user or group mapping for the affiliate application that maps your Windows account to the user name and password that are used to establish a connection with the Oracle database. Depending on your installation, a user might be able to perform this step or it might require someone with special types of SSO administrative privileges.  
  
> [!NOTE]
>  When configured for SSO, the WCF-Custom adapter uses services provided by SSO to get the Oracle user name and password from the SSO database. It provides these (unencrypted) to the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], so that the adapter can open a connection to the Oracle E-Business Suite. SSO provides no encryption or protection across the connection between the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] and the Oracle E-Business Suite.  
  
 For information about how to use SSO, including information about how to create affiliate applications and SSO mappings, see [Using SSO](../../core/using-sso.md). For more general information about SSO, see [Implementing Enterprise Single Sign-On](../../core/implementing-enterprise-single-sign-on.md). 
  
## The AcceptCredentialsInUri Binding Property  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] surfaces the **AcceptCredentialsInUri** binding property. This property determines whether Oracle database or Oracle E-Business Suite credentials are permitted in the connection URI. By default, **AcceptCredentialsInUri** is **false** and the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] throws an exception if credentials are included in the URI.  
  
 This property is surfaced because there are certain programming scenarios that require the credentials to be present in the connection URI. This should never be the case when you are configuring a send port or a receive location, or when you are using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to retrieve message schemas from the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. It is recommended that you do not set **AcceptCredentialsInUri** to **true**. For more information about the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
 The **AcceptCredentialsInUri** binding property is not available in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] in the **Binding** tab while configuring a WCF-Custom or WCF-OracleEBS receive or send port. To set the value of the **AcceptCredentialsInUri** binding property, you must open the adapter bindings file (XML file) that is created after you have generated metadata using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], and then locate this binding property in the file. Specify an appropriate value for this binding property, save the binding file, and then import the binding file in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. See [Importing Bindings](http://msdn.microsoft.com/library/7af35a2e-fb7c-48a1-af28-93427403a745) for instructions.  
  
## See Also  
 [Secure your Oracle EBS applications](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md)  
 [Best practices to secure the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/best-practices-to-secure-the-oracle-e-business-suite-adapter.md)
