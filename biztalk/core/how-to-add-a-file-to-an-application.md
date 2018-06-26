---
title: "How to Add a File to an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [applications], adding files"
  - "files, adding to applications"
  - "managing [resources], adding files"
ms.assetid: 6665b946-113a-4026-a0a3-6b67ede4b689
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a File to an Application
This topic describes how to use the BizTalk Server Administration console or the command line to add a file to a BizTalk application. Files that you add to your application are copied to the installation folder when the application is installed. Files can also can be exported into the application's .msi file and moved to different deployment environments with the application.  
  
> [!NOTE]
>  For instructions on adding a Readme file, see [How to Link to a Readme File](../core/how-to-link-to-a-readme-file.md).  
  
 If you want to overwrite a file that already exists in the application, specify the Overwrite option. The overwrite option only works when both files have the same file name. If not specified, and a file already exists in the application with the same file name as the one being added, the add operation will fail.  
  
> [!NOTE]
>  Unlike some other types of artifacts, you can have more than one file having the same file name in a BizTalk group.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To add a file to an application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] and the BizTalk Group containing the application to which you want to add the file.  
  
3. Expand Applications and the application to which you want to add a file.  
  
4. Right-click the **Resources** folder, point to **Add**, and then click **Resources**.  
  
5. Click **Add**, select the file, and then click **Open**.  
  
6. In the **File type** drop-down list, select **System.BizTalk:File**.  
  
7. In **Destination**, type the full path of the location where the file is to be copied when the application is installed from the .msi file, including the file name. The default is %BTAD_InstallDir%, the application installation folder. If this path is not provided, the file is not copied to the local file system during installation.  
  
8. When finished, click **OK**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:File** [**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:File /Overwrite /Source:"C:\Source Files\File.txt" /Destination:"C:\New Files\File.txt" /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the BizTalk application to which to add the file. If the application name is not specified, the default BizTalk application is used. If the name includes spaces, you must enclose it in double quotation marks (").|  
   |**/Type**|**System.BizTalk:File** (This value is not case-sensitive.)|  
   |**/Overwrite**|Option to update an existing file. If not specified, and a file already exists in the application that has the same name as the file being added, the AddResource operation fails.|  
   |**/Source**|Full path of the file, including the file name. If the path includes spaces, you must enclose it in double quotation marks (").|  
   |**/Destination**|Full path of the location where the file is to be copied when the application is installed from the .msi file. If the path includes spaces, you must enclose it in double quotation marks ("). If not provided, the file is not copied to the local file system during installation.|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource Command: File](../core/addresource-command-file.md)   
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)