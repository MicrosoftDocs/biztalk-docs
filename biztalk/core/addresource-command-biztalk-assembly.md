---
title: "AddResource Command: BizTalk Assembly | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c18607b5-d929-48c9-9fa3-f728a7a80d04
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AddResource Command: BizTalk Assembly
To add a BizTalk assembly to a BizTalk application, you use the **AddResource** command and specify **System.BizTalk:BizTalkAssembly** for the Type parameter. Running this command adds the assembly to the BizTalk Management database. The assembly is also displayed in the BizTalk Server Administration console, in the Resources folder of the application to which you added it. The artifacts included in the assembly are also displayed in the appropriate folders. In addition, the artifacts are listed when you use the [ListApp Command](../core/listapp-command.md).  
  
 When using this command, bear in mind the following points:  
  
- If an assembly has the same full name as an assembly that already exists in the application, you must specify the Overwrite parameter or the AddResource operation will fail. The full name consists of the name, public key token, culture, and version. If another application depends on this assembly, however, the AddResource operation will fail even if you specify the Overwrite parameter.  
  
- If another assembly having the same full name exists in the group, the AddResource operation will fail, even if you specify the Overwrite parameter.  
  
- If you are overwriting an assembly that contains orchestrations, the orchestrations must be stopped and unenlisted before you run this command. In addition, the send ports to which the orchestration is bound must be stopped and unenlisted, and the receive locations disabled.  
  
- If the assembly you are adding has a dependency on another artifact that is not included in the application, the AddResource operation will fail.  
  
  For more information about dependencies, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).  
  
## Usage  
 **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:BizTalkAssembly** [**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Options:GacOnAdd**<em>&#124;</em>**GacOnInstall**<em>&#124;</em>**GacOnImport**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Value|  
|---------------|--------------|-----------|  
|**/ApplicationName** (or **/A**, see Remarks)|No|Name of the BizTalk application to which to add the assembly. If the name includes spaces, you must enclose it in double quotation marks ("). If the application name is not specified, the default BizTalk application is used.|  
|**/Type** (or **/T**, see Remarks)|Yes|**System.BizTalk:BizTalkAssembly** (This value is not case-sensitive.)|  
|**/Overwrite** (or **/Ov**, see Remarks)|No|Option to update an existing assembly. If not specified, and an assembly already exists in the application that has the same full name as the assembly being added, the AddResource operation fails. The full name corresponds to the locally unique identifier (LUID) for the assembly. You can view the LUIDs for the artifacts in an application by using the [ListApp Command](../core/listapp-command.md). If another application depends on the assembly being overwritten, the AddResource operation fails, even when this parameter is specified.|  
|**/Source** (or **/So**, see Remarks)|Yes|Full path of the assembly file, including the file name. If the path includes spaces, you must enclose it in double quotation marks (").|  
|**/Destination** (or **/De**, see Remarks)|No|Full path of the location where the assembly file is to be copied when the application is installed from the .msi file. If not provided, the assembly file is not copied to the local file system during installation. If the path includes spaces, you must enclose it in double quotation marks ("). **Note:**  You can use the environment variable %BTAD_InstallDir%, which is set during BizTalk Server installation, to specify the application installation folder. This will create a consistent location for the application's files on different destination computers. Example: "%BTAD_InstallDir%\MyFiles\Orchestrations.dll"|  
|**/Options** (or **/Op**, see Remarks)|No|-   **GacOnAdd**: Specify to install the assembly to the global assembly cache (GAC) on the local computer during the AddResource operation.<br />-   **GacOnInstall**: Specify to install the assembly to the GAC when the application is installed from the .msi file.<br />-   **GacOnImport**: Specify to install the assembly to the GAC when the application .msi file is imported.<br /><br /> You must separate multiple options with a comma.|  
|**/Server** (or **/Se**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/Da**, see Remarks)|No|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:BizTalkAssembly /Overwrite**  
  
 **/Source:"%BTAD_InstallDir%\Source Assemblies\Orchestrations.dll" /Destination:"%BTAD_InstallDir%\New Assemblies\Orchestrations.dll" /Options:GacOnInstall,GacOnImport /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [AddResource Command](../core/addresource-command.md)   
 [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md)