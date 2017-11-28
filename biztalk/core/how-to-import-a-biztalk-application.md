---
title: "How to Import a BizTalk Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, planning"
  - "planning, importing"
  - "importing, applications"
  - "applications, planning"
  - "planning, deploying"
  - "applications, importing"
  - "importing, planning"
ms.assetid: 51169f35-d572-4612-9104-a59908e24874
caps.latest.revision: 70
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Import a BizTalk Application
This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or the command line import a BizTalk application into a BizTalk group. Importing a BizTalk application registers the artifacts in the BizTalk Management database and writes the data of the artifacts to the appropriate BizTalk databases. For details, see [What Happens When Artifacts Are Imported](../core/what-happens-when-artifacts-are-imported.md). Importing an application does not install the application. You must install an application that includes file-based artifacts before it can run.  
  
 When you use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to import an application, the location from which you start the Import MSI Wizard determines whether or not you can create a new application at the same time that you import the artifacts. If you start the wizard by right-clicking the BizTalk group, you must provide an application name. If an existing application in the BizTalk group has the name you specify, the artifacts in the file are imported into this application; otherwise, a new application having the specified name is created, and the artifacts are imported into it. If you start wizard by right-clicking an application, you cannot specify an application name, and the artifacts are imported into the current application.  
  
 When you use the BTSTask command-line tool to import an .msi file, providing an application name is optional. If you do not provide a name, its artifacts are imported into the default application.  
  
 After importing the artifacts, you can view them in the appropriate folder under the application's folder in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. You can also view a list of artifacts in the application by using BTSTask, as described in [ListApp Command](../core/listapp-command.md).  
  
## Prerequisites  
 To import a BizTalk application, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. To install a BizTalk application, you must also have Write permissions on the local file system. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## Considerations for importing applications  
 When importing an application, the following considerations may apply:  
  
-   **Importing applications from previous versions of BizTalk Server**. If you are importing applications from BizTalk Server 2006 R2 or BizTalk Server 2009, and the applications contain EDI/AS2 party data, the application import might fail because the trading partner management model has changed considerably in [!INCLUDE[prague](../includes/prague-md.md)]. You must instead use the Party Migration Tool to migrate the party data from previous BizTalk Server versions. For more information about the tool, see [Migrating EDI Artifacts from a Previous Version of BizTalk Server](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c).  
  
-   **Existing bindings are always overwritten by imported bindings.** When you import an .msi file that contains bindings into an existing application, the existing bindings are overwritten by imported bindings that have the same name. This is the case even when you have not selected the option to overwrite existing artifacts when importing the .msi file. If you do not want the bindings in the application you are exporting to overwrite the bindings in an application into which you are importing the .msi file, then you should not select the binding file as a resource to export during the export operation. For more information, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).  
  
     As bindings are applied during the import process, bindings that have already been applied are overwritten by new bindings that have the same name. In other words, the last binding of a particular name to be applied takes effect. When you import an application, bindings are applied in the following order:  
  
    1.  Application bindings generated by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that were not explicitly added to the application via a binding file, but that were explicitly selected by the user for export into the application .msi file.  
  
    2.  Binding files that have been explicitly added, and do not have a target deployment environment specified. Bindings in this set are applied in no specific order.  
  
    3.  Bindings that have been explicitly added, and that have an associated target deployment environment that matches the deployment environment selected for application import. Bindings in this set are applied in no specific order.  
  
-   **The host must exist in the group.** A host corresponding to the host specified in the application bindings contained in the .msi file must already exist in the BizTalk group or the import operation will fail. In addition, the host trust level must match.  
  
-   **You may need to add a reference to another application.** If the application you are importing depends on an artifact in another application, you need to add a reference to this application. The application and required artifact must already exist in the group. The Import Wizard provides this option. If you are using the ImportApp command of BTSTask, however, you must add the reference to the application after import, as described in [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md). For background information, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md). The Import Wizard matches the references to existing applications in the group and gives you the option to add a new reference or change an existing reference. You should take the additional step of verifying that the referenced application contains the required artifact.  
  
-   **If an import operation times out, split the application into additional .msi files.** An import operation will time out if it exceeds 3600 seconds in duration. If you are attempting to import an .msi file, and the operation times out, you should divide the contents of the application into more than one .msi file by re-exporting the application and selecting a subset of artifacts to export. For more information, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).  
  
> [!IMPORTANT]
>  For security reasons, during application export, passwords are removed from application bindings. They are not, however, removed from any binding files that were added to the application. After importing the application, you will need to reconfigure the passwords in order for the application to function. You can do this by editing the binding file or by using the administration console. For more information about editing a binding file, see [Customizing Binding Files](../core/customizing-binding-files.md). For more information about configuring security for adapters, see [Using Adapters](../core/using-adapters.md).  
  
> [!NOTE]
>  If an import fails, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] rolls back all import operations except for any actions performed by custom scripts.  
  
> [!NOTE]
>  If you create a filter for a send port in one application that uses a property schema in another application, and then import the first application into a new BizTalk group, you will not receive a warning that the schema is missing, and filtering will not function when the application is installed and started. You can correct the problem by importing the application that contains the schema before you install the application that does not contain the schema.  
  
## To import a BizTalk application  
  
#### Using the BizTalk Server Administration Console  
  
1.  Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2.  In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and do one of the following:  
  
    -   To import the application and artifacts contained in the .msi file into the BizTalk group, right-click **Applications**, point to **Import**, and then click **MSI file**.  
  
    -   To import the artifacts contained in the .msi file into an existing application, expand **Applications**, right-click the application, point to **Import**, and then click **MSI file**.  
  
3.  On the Welcome to the Import MSI Wizard page, in **MSI file to import**, type the path of the .msi file, and then click **Next**. If necessary, you can browse for the .msi file by clicking the **…** button.  
  
4.  On the Application Settings page, in the **Application name** drop-down list, select the application name, if available. The list is available if you are importing the application into the BizTalk group.  
  
    > [!NOTE]
    >  The list includes the names of all of the applications currently in the BizTalk group as well as the application from which the .msi file was exported. If you select the latter application name, and the application does not already exist in this BizTalk group, the Import Wizard creates a new application. If you select an application that already exists in the group, the Import Wizard imports the artifacts from the .msi file into the existing application.  
  
5.  In **Available applications to add references to**, select the applications to which to add references, if any, and then click **Next**.  
  
6.  If you are importing the .msi file into an existing application and want to overwrite artifacts in the existing application, select **Overwrite resources**.  
  
    > [!NOTE]
    >  If you do not select this option, and the .msi file contains an artifact that already exists in the application, the import operation will fail and roll back. Certain types of artifacts in a BizTalk application or group must be unique. If you are adding an artifact that already exists in the BizTalk group, but not in the current application, the import operation will fail, even if you specify the overwrite option. For more information about which artifacts must be unique and in what ways they must be unique, see [Artifacts That Must Be Unique in an Application or Group](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).  
  
7.  On the Application Target Environment Settings page, in the **Target Staging Environment** drop-down list, select the target environment for this application, and click **Next**. This list contains all environments that have been specified for any binding files that have been added to this application. Select \<Default\> if you want to apply all bindings in the application except for those that have a target environment specified. If the .msi file does not contain a binding file that you want to apply explicitly, you can leave \<Default\> selected.  
  
    > [!NOTE]
    >  You specify the target environment for bindings when you add a binding file to an application. For background information, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md). For instructions on adding binding files, see [How to Add a Binding File to an Application](../core/how-to-add-a-binding-file-to-an-application2.md).  
  
8.  On the Import Summary page, confirm that the summary information is correct, and then click **Import**.  
  
9. On the Import Succeeded page, if you want to install the application on the local computer, select the **Run the Application Installation Wizard to install the application on the local computer** check box.  
  
    > [!NOTE]
    >  Unless you need to run the application as it is currently configured on the local computer, you do not need to install it. If the application includes file-based artifacts, however, you must install the application on all of the computers that will run it before it can begin functioning, as importing the application only adds it to the BizTalk Management database.  
  
10. Click **Finish**.  
  
> [!NOTE]
>  If the installation fails, for example because you do not have Write permissions on the local file system, the installation is rolled back, but not the import operation.  
  
#### Using the command line  
  
1.  Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  Type the following command, substituting the appropriate values, as described in the following table:  
  
     **BTSTask ImportApp /Package:** *value* [**/Environment:***value*] [**/ApplicationName:***value*] [**/Overwrite**] [**/Server:***value*] [**/Database:***value*]  
  
     Example:  
  
     **BTSTask ImportApp /Package:"C:\MSI Files\MyApplication.msi"  /Environment:Test /ApplicationName:MyApplication /Overwrite**  
  
    |Parameter|Value|  
    |---------------|-----------|  
    |**/Package**|Full path of the .msi file. If the path includes spaces, you must enclose it in quotation marks (").|  
    |**/Environment**|The target deployment environment of the binding file to apply, such as Test. This is the value that was specified for the target deployment environment when the binding file was added to the application.|  
    |**/ApplicationName**|Name of the BizTalk application to which the artifacts in the .msi file are imported. If not specified, the application name that was specified when exporting the .msi file is used. If the specified application does not exist, it will be created. Application names that include spaces must be enclosed with double quotation marks (").|  
    |**/Overwrite**|Option to overwrite artifacts in the application with artifacts in the .msi file that have the same locally unique identifier (LUID). If this option is not specified, and there are one or more artifacts in the application that have the same LUID as artifacts in the .msi file, the import fails. You can view the LUIDs of the artifacts in an application by using the [ListApp Command](../core/listapp-command.md).|  
    |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
    |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [ImportApp Command](../core/importapp-command.md)