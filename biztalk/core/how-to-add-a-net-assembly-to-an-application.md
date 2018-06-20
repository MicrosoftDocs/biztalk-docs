---
title: "How to Add a .NET Assembly to an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [.NET assemblies], adding to applications"
  - "managing [applications], .NET assemblies"
  - "managing [.NET assemblies], applications"
  - "applications, .NET assemblies"
  - ".NET assemblies, adding to applications"
ms.assetid: 75dc3303-a622-40df-881e-3109cbc81c91
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a .NET Assembly to an Application
This topic describes how to use the BizTalk Server Administration console or the command line to add a .NET assembly that is not a BizTalk assembly to a BizTalk application. When adding a .NET assembly to an application, bear in mind the following important points:  
  
-   If you want to overwrite an assembly that already exists in the application, specify the Overwrite option. The overwrite option is necessary only when both assemblies have the same LUID. If not specified, and an assembly already exists in the application with the same LUID as the assembly being added, the add operation will fail. You can view the LUIDs for the artifacts in an application by using the [ListApp Command](../core/listapp-command.md).  
  
-   When you add a .NET assembly, you can specify one or more of the following options for installing the assembly to the global assembly cache (GAC):  
  
    -   **Add to the global assembly cache on add resource (gacutil).** When you select this option, the assembly is installed in the GAC on the local computer when the assembly is added to an application, as a result of using the procedures in this topic.  
  
    -   **Add to the global assembly cache on MSI file import (gacutil).** When you select this option, if the application is exported to an .msi file, and the .msi file is imported into a BizTalk group, the assembly is installed in the GAC on the local computer as part of the import process. Select this option when your application includes a policy as well as an assembly upon which the policy depends. You need to do this because, when you import an application containing a policy, any assemblies that the policy depends upon must be present in the GAC.  
  
    -   **Add to the global assembly cache on MSI file install (gacutil).** When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, the assembly is installed in the GAC on the local computer as part of the installation process.  
  
    -   **Make visible to COM components (regasm).** When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, a managed COM assembly is added to the Windows registry on the local computer as part of the installation process. If you specify this option, you must also specify a location for the file in Destination.  
  
    -   **Register serviced components (regsvcs).** When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, a managed COM+ assembly is added to the Windows registry on the local computer as part of the installation process. If you specify this option, you must also specify a location for the file in Destination.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To add a .NET assembly to an application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application to which you want to add the .NET assembly.  
  
3. Right-click the **Resources** folder, point to **Add**, and then click **Resources**.  
  
4. Click **Add**, click the assembly, and then click **Open**.  
  
5. In the **File type** drop-down list, select **System.BizTalk:Assembly**.  
  
6. In **Options**, select the deployment options for this assembly.  
  
7. In **Destination**, type the full path of the location where the file is to be copied when the application is installed from the .msi file, including the file name. If this path is not provided, the file is not copied to the local file system during installation. To copy the file to the application installation folder, you can use the %BTAD_InstallDir% environment variable in the path, which takes the value of the application installation folder when the application is installed. This way, you do not need to know the path of the application installation folder when you specify the destination location.  
  
    Example: **%BTADInstall_Dir%\Assemblies\Orchestrations.dll**  
  
8. Click the **Dependencies** tab and view the artifacts on which this assembly depends.  
  
9. If an artifact on which this assembly depends is not present in this application, and you want to add it, click **Add to Application**, browse to the artifact, and then click **Open**.  
  
10. When finished, click **OK**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table.  
  
    **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:Assembly** [**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Options:GacOnAdd**<em>&#124;</em>**GacOnInstall**<em>&#124;</em>**GacOnImport**&#124;**RegasmOnInstall**&#124;**RegsvcsOnInstall**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:Assembly /Overwrite /Source:"C:\Source Assemblies\MyAssembly.dll" /Destination:"%BTAD_InstallDir%\New Assemblies\MyAssembly.dll" /Options:GacOnAdd,RegasmOnInstall /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the BizTalk application to which to add the assembly. If the application name is not specified, the default BizTalk application for the group is used. If the name includes spaces, you must enclose it in double quotation marks (").|  
   |**/Type**|**System.BizTalk:Assembly** (This value is not case-sensitive.)|  
   |**/Overwrite**|Option to update an existing assembly. If not specified, and an assembly already exists in the application that has the same full name as the assembly being added, the AddResource operation fails. The full name includes the assembly file name, version, culture, and public key token. You can view the LUIDs for the artifacts in an application by using the [ListApp Command](../core/listapp-command.md).|  
   |**/Source**|Full path of the assembly file, including the file name. If the path includes spaces, you must enclose it with double quotation marks (").|  
   |**/Destination**|Full path of the location where the assembly file is to be copied when the application is installed from the .msi file. If not provided, the assembly file is not copied to the local file system during installation. If the path has spaces, you must enclose it with double quotation marks ("). If you specify the RegasmOnInstall or RegsvcsOnInstall option, you must also specify Destination. **Note:**  You can use the %BTAD_InstallDir% environment variable in the path. It takes the value of the application installation folder when the application is installed. This way, you do not need to know the path of the application installation folder when you specify the destination location. Example: %BTAD_InstallDir%\Assemblies\Orchestrations.dll|  
   |**/Options**|-   **GacOnAdd**: Install the assembly to the global assembly cache (GAC) on the local computer during the AddResource operation.<br />-   **GacOnInstall**: Install the assembly to the GAC when the application is installed from the .msi file.<br />-   **GacOnImport**: Install the assembly to the GAC when the application .msi file is imported.<br />-   **RegasmOnInstall**: Add a managed COM assembly to the Windows registry when the application is installed from the .msi file. If you specify this option, you must also specify Destination.<br />-   **RegsvcsOnInstall**:Add a managed COM+ assembly to the Windows registry when the application is installed from the .msi file. If you specify this option, you must also specify Destination.<br /><br /> You must separate multiple options with a comma.|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource Command: .NET Assembly](../core/addresource-command-net-assembly.md)   
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)