---
title: "AddResource Command: .NET Assembly | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef6ec298-35fe-4845-9549-685993d2c659
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AddResource Command: .NET Assembly
To add a .NET assembly (which includes managed COM or COM+ components) to a BizTalk application, you use the **AddResource** command and specify **System.BizTalk:Assembly** for the Type parameter. Running this command adds the assembly to the BizTalk Management database. The assembly is also displayed in the BizTalk Administration console, in the Resources folder of the application to which you added it. In addition, the assembly is listed when you use the [ListApp Command](../core/listapp-command.md).  
  
 If an assembly has the same full name as an assembly that already exists in the application, you can specify the Overwrite parameter. The full name consists of the name, public key token, culture, and version. In this case, the existing assembly is overwritten. For more information about dependencies, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).  
  
## Usage  
 **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:Assembly**[**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Options:GacOnAdd**<em>&#124;</em>**GacOnInstall**<em>&#124;</em>**GacOnImport**&#124;**RegasmOnInstall**&#124;**RegsvcsOnInstall**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Value|  
|---------------|--------------|-----------|  
|**/ApplicationName** (or **/A**, see Remarks)|No|Name of the BizTalk application to which to add the assembly. If the name includes spaces, you must enclose it in double quotation marks ("). If the application name is not specified, the default BizTalk application for the group is used.|  
|**/Type** (or **/T**, see Remarks)|Yes|**System.BizTalk:Assembly** (This value is not case-sensitive.)|  
|**/Overwrite** (or **/Ov**, see Remarks)|No|Option to update an existing assembly. If not specified, and an assembly already exists in the application that has the same full name as the assembly being added, the AddResource operation fails. The full name includes the assembly name, version, culture, and public key token. This information is displayed in the Name field of the application's Resources folder within the BizTalk Server Administration console.|  
|**/Source** (or **/So**, see Remarks)|Yes|Full path of the assembly file, including the file name. If the path includes spaces, you must enclose it with double quotation marks (").|  
|**/Destination** (or **/De**, see Remarks)|No|Full path of the location where the assembly file is to be copied when the application is installed from the .msi file. If not provided, the assembly file is not copied to the local file system during installation. If the path includes spaces, you must enclose it with double quotation marks ("). If you specify the RegasmOnInstall or RegsvcsOnInstall option, you must also specify Destination. **Note:**  You can use the %BTAD_InstallDir% environment variable to specify the application installation folder. This creates a consistent location for the application's files on different destination computers. Example: "%BTAD_InstallDir%\MyAssemblies\Orchestrations.dll"|  
|**/Options** (or **/Op**, see Remarks)|No|-   **GacOnAdd**: Install the assembly to the global assembly cache (GAC) on the local computer during the AddResource operation.<br />-   **GacOnInstall**: Install the assembly to the GAC when the application is installed from the .msi file.<br />-   **GacOnImport**: Install the assembly to the GAC when the application .msi file is imported.<br />-   **RegasmOnInstall**: Add a managed COM assembly to the Windows registry when the application is installed from the .msi file. If you specify this option, you must also specify Destination.<br />-   **RegsvcsOnInstall**:Add a managed COM+ assembly to the Windows registry when the application is installed from the .msi file. If you specify this option, you must also specify Destination.<br /><br /> You must separate multiple options with a comma. There can be no spaces between commas and values.|  
|**/Server** (or **/Se**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/Da**, see Remarks)|No|Name of the BizTalk Management database. If not provided, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **BTSTask AddResource /ApplicationName:MyApplication /Type: System.BizTalk:Assembly  /Overwrite /Source:"%BTAD_InstallDir%\Source Assemblies\MyAssembly.dll" /Destination:"%BTAD_InstallDir%\New Assemblies\MyAssembly.dll" /Options:GacOnAdd,RegasmOnInstall /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [AddResource Command](../core/addresource-command.md)   
 [How to Add a .NET Assembly to an Application](../core/how-to-add-a-net-assembly-to-an-application.md)