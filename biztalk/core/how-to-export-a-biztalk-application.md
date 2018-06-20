---
title: "How to Export a BizTalk Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, exporting"
  - "exporting, warnings"
  - "exporting, applications"
  - "applications, exporting"
  - "applications, security"
  - "applications, warnings"
  - "exporting, security"
ms.assetid: a1d6ffca-3d29-44c7-a811-6cf8b42e23f6
caps.latest.revision: 50
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Export a BizTalk Application
This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or the command line to export an application. Exporting a BizTalk application generates a Windows Installer (.msi) file that contains the application and any of its artifacts that you select to export. The default option is to select all of the application's artifacts, but you can select a subset of them. You can then import the .msi file into another BizTalk group to add the artifacts to an existing application in the new group, update the artifacts in an existing application, or create a new application in the group that contains the artifacts being imported. For more information, see [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md). You also use the .msi file to install the application on the computers that will run it, as described in [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md). If the application includes file-based artifacts, you must also install it before it can begin functioning.  
  
 When exporting an application, bear in mind the following important points:  
  
- **Existing bindings are automatically overwritten by imported bindings.** If you do not want the bindings in the application you are exporting to overwrite the bindings in an application into which you are importing an .msi file, then you should not select the binding file as a resource to export. When you import an .msi file that contains a binding file into an existing application, the existing bindings are overwritten by the ones being imported, even when you have not selected the option to overwrite existing artifacts.  
  
- **A user may be making changes to an artifact while you are exporting the application.** If a user is modifying a database-based artifact, such as a virtual directory, certificate, or policy, while an export operation is in progress, the changes will not be reflected in the exported .msi file. Therefore, we recommend that you schedule export operations during hours when users are not likely to be making changes to these artifacts.  
  
- **Incorrect error can be displayed when installing an .msi on Windows Vista**. When installing an .msi package exported using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you may receive the following incorrect error, "The installer has encountered an unexpected error installing this package. This may indicate a problem with this package. The error code is 2869." To correct this error, first import the .msi package using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and then re-export and install the package.  
  
- **The application may have dependencies on another application.** This can affect how you deploy the application. For more information, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).  
  
- **You can modify the destination directory of resources in your application prior to export.** If you want to change the destination location, expand the resources node of your application, right-click the resource you want to change, and then choose **Modify**. In the Modify Resources dialog, enter a new location in for **Destination location**.  
  
- **Export will fail if the application contains a policy that has been removed from the Rule Engine database.** When you remove a policy from the Rule Engine database by using the Rule Engine Deployment Wizard, it will display in the administration console in a "Not Published" state, and you will not be able to export the application. For more information about the Rule Engine Deployment Wizard, see [How to Deploy and Undeploy Policies and Vocabularies](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).  
  
> [!IMPORTANT]
>  The .msi file may contain sensitive data. Be sure to take steps to ensure that the file is secure. For more information, see [Security and Windows Installer](../core/security-and-windows-installer.md).  
> 
>  During application export, passwords are removed from application bindings. After installing the application from the .msi file, you will need to reconfigure the passwords in order for the application to function. Passwords are not removed, however, from any binding files that you added to the application.  
> 
>  If the application includes a Web site or an orchestration that uses a Web service, be aware that the security settings on the virtual directory are those in effect when the .msi file is generated during application export. If you are deploying an application to a production environment, then before exporting the application, you should verify that the settings meet your security requirements. If the virtual directory already exists on the host computer, its security settings are not overwritten, but the files in the application will be added to it. You should verify the security settings after the application is imported.  
> 
>  All discretionary access control lists (DACLs) are removed from files and folders when an application is exported. After installing an application, you must reconfigure all security settings on the files and folders, including virtual directories.  
> 
> [!NOTE]
>  If an export operation fails, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deletes all temporary files along with the .msi file, if one was created.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md). In addition, the Business Rules Engine must be installed. For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).  
  
## To export an application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, and then expand **Applications**.  
  
3. Right-click the application that you want to export, point to **Export**, and then click **MSI file**.  
  
4. On the Welcome to the Export MSI File Wizard page, click **Next**.  
  
5. On the Select Resources page, select the artifacts to export into the .msi file, and then click **Next**.  
  
6. If prompted, on the Specify IIS Hosts page, type the server name of the computer hosting the virtual directory that you want to include, and then click **Next**. You will be prompted to specify the server only if the virtual directory has not been previously added to the BizTalk Management database, such as when it was added to the application or it was imported in an application.  
  
7. On the Dependencies page, review the dependencies for the application, and then click **Next**.  
  
8. On the Destination page, in **Destination application name**, type the application name.  
  
9. In **MSI file to generate**, type the full path for the .msi file, and then click **Export**. Example: C:\MSI\Errorhandling.msi  
  
    > [!NOTE]
    >  We recommend that you store .msi files in a secure folder.  
  
10. On the Summary page, make a note of the location of the log file for this operation, and then click **Finish**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask ExportApp** [**/ApplicationName:**<em>value</em>] **/Package:**<em>value</em> [**ResourceSpec:**<em>value</em> [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
    Example:  
  
    **BTSTask ExportApp /ApplicationName:MyApplication /Package:C:/MSI/MyApplication.msi /ResourceSpec:"C:\My Files\ResourceSpec.xml" /Server:MySQLServer /Database:BizTalkMgmtDb**  
  
    The artifacts you specified are exported into an .msi file in the location you specified.  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the BizTalk application to export. If the application name is not specified, the default BizTalk application is used. If the name includes spaces, it must be enclosed with double quotation marks (").|  
   |**/Package**|Path of the .msi file to be created, including its file name.|  
   |**/ResourceSpec**|Path of the resource specification XML file, including file name. You can specify which artifacts to export by editing the resource specification XML file, which is created when you run the ListApp command with the ResourceSpec parameter, as described in [ListApp Command](../core/listapp-command.md). You must manually edit this file to add the Internet Information Services (IIS) host server name for a virtual directory that you want to export if the Web server is on a remote computer.|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Exporting BizTalk Applications, Bindings, and Policies](../core/exporting-biztalk-applications-bindings-and-policies.md)   
 [ExportApp Command](../core/exportapp-command.md)