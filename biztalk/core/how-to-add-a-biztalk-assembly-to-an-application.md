---
title: "How to Add a BizTalk Assembly to an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [applications], adding assemblies"
  - "assemblies, applications"
  - "managing [assemblies], adding to applications"
  - "applications, assemblies"
  - "managing [assemblies], applications"
ms.assetid: 1525a0f6-cb0f-43bf-a851-40c06ab2135e
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a BizTalk Assembly to an Application
This topic describes how to use the BizTalk Server Administration console or the command line to add a BizTalk assembly to an application.  
  
 When adding the BizTalk assembly to an application, bear in mind the following important points:  
  
-   If you want to add an assembly and overwrite an assembly with the same locally unique identifier (LUID) that already exists in the application, specify the Overwrite option. If not specified, and an assembly that has the same LUID as the assembly being added already exists in the application the operation will fail. The LUID includes the assembly file name, version, culture, and public key token. You can view the LUIDs for the artifacts in an application by using the [ListApp Command](../core/listapp-command.md).  
  
-   If the assembly you are adding has a dependency on another artifact that is not included in the application, the add operation will fail.  
  
-   When you add a BizTalk assembly, you can specify one or more of the following options for installing the assembly to the global assembly cache (GAC):  
  
    -   **Add to the global assembly cache on add resource (gacutil).** When you select this option, the assembly is installed in the GAC on the local computer when the assembly is added to an application, as a result of using the procedures in this topic.  
  
    -   **Add to the global assembly cache on MSI file import (gacutil).** When you select this option, if the application is exported to an .msi file, and the .msi file is imported into a BizTalk group, the assembly is installed in the GAC on the local computer as part of the import process.  
  
    -   **Add to the global assembly cache on MSI file install (gacutil).** When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, the assembly is installed in the GAC on the local computer as part of the installation process.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To add a BizTalk assembly to an application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand BizTalk Server Administration and the BizTalk Group containing the application to which you want to add the BizTalk assembly.  
  
3. Expand Applications and the application to which you want to add a BizTalk assembly.  
  
4. Right-click **Resources**, point to **Add** and then click **BizTalk Assemblies**.  
  
5. Click **Add**, select the BizTalk assembly file, and then click **Open**.  
  
6. In **Destination**, type the full path of the location where the assembly file is to be copied when the application is installed from the .msi file, including the file name. If not provided, the assembly file is not copied to the local file system during installation.  
  
7. In **Options**, specify the options for installing the BizTalk assembly to the GAC, and then click **OK**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:BizTalkAssembly** [**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Options:GacOnAdd**&#124;**GacOnInstall**&#124;**GacOnImport**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:BizTalkAssembly /Overwrite /Source:"C:\BizTalk Assemblies\MyOrchestration.dll" /Destination:"C:\New BizTalk Assemblies\ MyOrchestration.dll " /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the BizTalk application to which to add the BizTalk assembly. If the application name is not specified, the default BizTalk application is used. If the name includes spaces, you must enclose it in double quotation marks (").|  
   |**/Type**|**System.BizTalk:BizTalkAssembly**|  
   |**/Overwrite**|Option to update an existing assembly. If not specified, and an assembly already exists in the application that has the same LUID as the assembly being added, the AddResource operation fails. You can view the LUIDs for the artifacts in an application by using the [ListApp Command](../core/listapp-command.md). If another application depends on the assembly being overwritten, the AddResource operation fails, even when this parameter is specified.|  
   |**/Source**|Full path of the assembly file, including the file name. If the path includes spaces, you must enclose it in double quotation marks (").|  
   |**/Destination**|Full path of the location where the assembly file is to be copied when the application is installed from the .msi file. If not provided, the assembly file is not copied to the local file system during installation. If the path includes spaces, you must enclose it in double quotation marks (").|  
   |**/Options**|-   **GacOnAdd**: Specify to install the assembly to the global assembly cache (GAC) on the local computer during the AddResource operation.<br />-   **GacOnInstall**: Specify to install the assembly to the GAC when the application is installed from the .msi file.<br />-   **GacOnImport**: Specify to install the assembly to the GAC when the application .msi file is imported.<br /><br /> You must separate multiple options with a comma.|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Managing BizTalk Assemblies](../core/managing-biztalk-assemblies.md)   
 [AddResource Command: BizTalk Assembly](../core/addresource-command-biztalk-assembly.md)