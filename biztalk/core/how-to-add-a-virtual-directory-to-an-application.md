---
title: "How to Add a Virtual Directory to an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "virtual directories"
  - "managing [applications], virtual directories"
  - "applications, virtual directories"
  - "virtual directories, applications"
ms.assetid: a5726696-bd65-49d9-8814-a078afe8c067
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a Virtual Directory to an Application
This topic describes how to use the BTSTask command-line tool to add a virtual directory to a BizTalk application. This option is not available in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. You might want to add a virtual directory if you have written a custom Web service or created an ASP.NET Web site for interfacing with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and want to deploy the virtual directory with the application.  
  
 Another way to add a virtual directory to an application is by specifying a virtual directory for a SOAP or HTTP receive location, as described in [How to Configure an HTTP Receive Location](../core/how-to-configure-an-http-receive-location.md). In all cases, the virtual directory is added to the BizTalk Management database. When you add a virtual directory by using the command line, it also displays in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, in the Resources folder of the application to which you added it as well as the list of artifacts in the application when you use the [ListApp Command](../core/listapp-command.md). If you later export the application and then import it into another BizTalk group, the virtual directory displays in the Resources folder.  
  
 When adding a virtual directory to an application, bear in mind the following points:  
  
-   You can overwrite a virtual directory that already exists in the application by specifying the overwrite option. The overwrite option is required only when the existing virtual directory has the same name as the one you want to add. If not specified, and a virtual directory already exists in the application with the same name as the one being added, the add operation will fail.  
  
-   When you add a virtual directory with a URL that contains https, you must use http in the URL that you specify rather than https. If you use https, the operation to add a virtual directory will fail. Even though you add it with http in the URL, the https setting for the URL in the Internet Information Services metabase will be in effect, and the virtual directory will function correctly.  
  
-   If you add a virtual directory from a 64-bit version of the Web service, and you attempt to install the application that includes the virtual directory on a 32-bit computer, the virtual directory will not be installed. It must be installed on a 64-bit computer.  
  
> [!IMPORTANT]
>  When you import an application containing a virtual directory, the security settings on the virtual directory are those in effect when the .msi file is generated during application export. If you are deploying an application into a production environment, before exporting the application, you should verify that the settings meet your security requirements.  
>   
>  If, however, the virtual directory already exists in the destination environment, the security settings on the existing virtual directory will be in effect. They are not changed to match those on the virtual directory you are deploying. In this case, you should verify that the security settings on the existing virtual directory meet your requirements.  
  
> [!CAUTION]
>  If the virtual directory uses the HTTPS (Hypertext Transfer Protocol over Secure Socket Layer) protocol, its security settings are not preserved during export, and when it is imported, the virtual directory will inherit the security settings of the root. You should verify that the security settings meet your requirements.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To add a virtual directory to an application  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask AddResource** [/**ApplicationName:**<em>value</em>] **/Type:System.BizTalk:WebDirectory**[**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask AddResource /ApplicationName:MyApplication /Type: System.BizTalk:WebDirectory /Overwrite /Source:<http://Host1:90/MyVirtualDirectory> /Destination:<http://Host2:90/MyVirtualDirectory> /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the BizTalk application to which to add the virtual directory. If the application name is not specified, the default BizTalk application for the group is used. If the name includes spaces, you must enclose it in double quotation marks (").|  
   |**/Type**|**System.BizTalk:WebDirectory** (This value is not case-sensitive.)|  
   |**/Overwrite**|Option to update an existing virtual directory. If not specified, and a virtual directory already exists in the application that has the same name as the virtual directory being added, the AddResources operation fails.|  
   |**/Source**|URI of the source virtual directory.|  
   |**/Destination**|URI to be assigned to the virtual directory when the application is installed from the .msi file. If this parameter is not specified, then the value of the Source parameter is used with localhost as the host.|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource Command: Virtual Directory](../core/addresource-command-virtual-directory.md)   
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)