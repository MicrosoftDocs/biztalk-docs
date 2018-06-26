---
title: "How to Add a Certificate to an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications, certificates"
  - "managing [certificates], adding to applications"
  - "certificates, applications"
  - "managing [applications], certificates"
  - "managing [certificates], applications"
  - "managing [resources], certificates"
ms.assetid: 7c615002-6627-4134-9c2b-bf1c89d626c2
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a Certificate to an Application
This topic describes how to use the command line to add a certificate to a BizTalk application. This option is not available in the BizTalk Server Administration console. You add a certificate to a BizTalk application so that you can transport the certificate from one BizTalk group to another, packaged with an application. You use certificates to verify identities and to establish secure links for send ports and receive locations. For more information, see [How to Assign a Certificate to a Send Port](../core/how-to-assign-a-certificate-to-a-send-port.md) and [How to Assign a Certificate to a Receive Location](../core/how-to-assign-a-certificate-to-a-receive-location.md).  
  
 When adding a certificate to an application, bear in mind the following important points:  
  
-   When you add a certificate to an application, the certificate is added to the BizTalk Management database as a certificate artifact. When you install the application, the certificate is imported into the Other People certificate store on the local computer, so you may not need to take the additional step of importing it into this store before you can assign it to a send port or receive location. When you use BTSTask to add the certificate, the certificate must exist in the Other People certificate store, and you must specify its thumbprint.  
  
    > [!NOTE]
    >  When a certificate is exported, the private key is removed. When the application is installed, although the certificate is imported into the certificate store, it cannot be used to decrypt an encrypted message, although it can be used to send an encrypted message. If you need to use the certificate for the former purpose, you should reinstall it in the Other People certificate store on the computer hosting the send port that uses the certificate.  
  
-   As a best practice, if a certificate will be used by a send port or receive location in two or more applications, you should deploy the certificate in a separate application, and then reference this application from the applications that need to use the certificate. This is because only one certificate having a particular thumbprint can exist in the BizTalk group, so you will not be able to import the same certificate in two different applications. If you attempt to import two applications that each use the same certificate, the first import will succeed, and the second will not. In this case, using the Overwrite import option does not correct the problem, as the existing certificate that you want to overwrite is contained in another application.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To add a certificate to an application  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:Certificate** [**/Overwrite**] **/Thumbprint:"**<em>value</em>**"** [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:Certificate /Overwrite /Thumbprint:"04 a2 8e 32 24 f9 36 b9 42 81 12 71 3a d2 ef db c7 9c 83 dc" /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the BizTalk application to which to add the certificate. If the application name is not specified, the default BizTalk application for the group is used. If the name includes spaces, you must enclose it in double quotation marks (").|  
   |**/Type**|**System.BizTalk:Certificate** (This value is not case-sensitive.)|  
   |**/Overwrite**|Option to update an existing certificate. If not specified, and a certificate already exists in the application that has the same Thumbprint property as the certificate being added, the Add operation fails. You can view the Thumbprint property by double-clicking the certificate in the Certificates snap-in and clicking the Details tab. For more information, see "Viewing certificate information" in the documentation for the Certificates snap-in.|  
   |**/Thumbprint**|Thumbprint property of the certificate (a *thumbprint* is a digest of data). This value must be enclosed in double quotation marks (").|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource Command: Certificate](../core/addresource-command-certificate.md)   
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)