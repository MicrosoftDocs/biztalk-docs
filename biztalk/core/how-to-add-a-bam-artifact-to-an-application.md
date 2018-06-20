---
title: "How to Add a BAM Artifact to an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications, definition files [BAM]"
  - "BAM, applications"
  - "managing [applications], definition files [BAM]"
  - "definition files [BAM], managing"
ms.assetid: 86f19030-e510-4527-ba74-10498c361c00
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a BAM Artifact to an Application
This topic describes how to use the BizTalk Server Administration console or the command line to add a BAM artifact to a BizTalk application. Adding a BAM definition file does not deploy the BAM definition. The BAM definition is deployed when the application .msi file is imported.  
  
 If you want to overwrite a BAM artifact that already exists in the application, specify the overwrite option. The overwrite option is required only when the existing BAM artifact has the same file name as the one you want to add. If not specified, and BAM artifact already exists in the application with the same file name as the one being added, the add operation will fail.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To add a BAM artifact to an application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **Al Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk Group, expand Applications, and then expand the application to which you want to add a BAM artifact file.  
  
3. Right-click the **Resources** folder, point to **Add**, and then click **Resources**.  
  
4. Click **Add**, select the file of the BAM artifact, and then click **Open**.  
  
5. In the **File type** drop-down list, select **System.BizTalk:BAM**.  
  
6. In **Destination**, type the full path of the location where the artifact file is to be copied when the application is installed from the .msi file, including the file name. If this path is not provided, the file is not copied to the local file system during installation, but it will be deployed when the application .msi file is imported.  
  
    Example: **C:\My Applications\MyBAMfile.xml**  
  
7. When finished, click **OK**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:Bam** [**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:Bam /Overwrite /Source:"C:\Source BAMfiles\MyBAMfile.xml" /Destination:"%BTADInstallDir%\ BAMfiles\MyBAMfile.xml" /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the BizTalk application to which to add the BAM artifact. If the application name is not specified, the default BizTalk application for the group is used. If the name includes spaces, you must enclose it in double quotation marks (").|  
   |**/Type**|**System.BizTalk:Bam** (This value is not case-sensitive.)|  
   |**/Overwrite**|Option to overwrite an existing BAM artifact. If not specified, and a BAM artifact already exists in the application that has the same file name as the BAM artifact being added, the AddResource operation fails.|  
   |**/Source**|Full path of the BAM artifact file, including the file name. If the path includes spaces, you must enclose it in double quotation marks (").|  
   |**/Destination**|Full path of the location where the BAM artifact file is to be copied when the application is installed from the .msi file. If not provided, the file is not copied to the local file system during installation. If the path includes spaces, you must enclose it in double quotation marks ("). You can use the environment variable %BTADInstallDir% in the path to specify the application installation folder.|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource Command: BAM Artifact](../core/addresource-command-bam-artifact.md)   
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)   
 [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md)