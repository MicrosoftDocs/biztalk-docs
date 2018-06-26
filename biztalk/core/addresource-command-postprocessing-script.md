---
title: "AddResource Command: Postprocessing Script | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d6d1622-1c90-4059-903e-68dcab829744
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AddResource Command: Postprocessing Script
To add a postprocessing script to a BizTalk application, you use the **AddResource** command and specify **System.BizTalk:PostProcessingScript** for the Type parameter. Running this command adds the script file to the BizTalk Management database. The script file is also displayed in the BizTalk Administration console, in the Resources folder of the application to which you added it. In addition, the file is listed when you use the [ListApp Command](../core/listapp-command.md).  
  
 A postprocessing script runs from the .msi file after the application import or installation, or before uninstallation. You can also use BTSTask to add a preprocessing script, which runs before application import or installation, or after uninstallation, as described in [AddResource Command: Preprocessing Script](../core/addresource-command-preprocessing-script.md). For more information about preprocessing and postprocessing scripts, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
## Usage  
 **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:PostProcessingScript**[**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>][**/Property:Args="**<em>argument list</em>**"**]  
  
## Parameters  
  
|Parameter|Required|Value|  
|---------------|--------------|-----------|  
|**/ApplicationName** (or **/A**, see Remarks)|No|Name of the BizTalk application to which to add the script. If the name includes spaces, you must enclose it in double quotation marks ("). If the application name is not specified, the default BizTalk application for the group is used.|  
|**/Type** (or **/T**, see Remarks)|Yes|**System.BizTalk:PostProcessingScript** (This value is not case-sensitive.)|  
|**/Overwrite** (or **/O**, see Remarks)|No|Option to update an existing script. If not specified, and a script file already exists in the application that has the same name as the script file being added, the add operation fails.|  
|**/Source** (or **/So**, see Remarks)|Yes|Full path of the script file, including the file name. If the path includes spaces, you must enclose it in double quotation marks (").|  
|**/Destination** (or **/De**, see Remarks)|No|Full path of the location where the script file is to be copied when the application is installed from the .msi file. If not provided, the file is not copied to the local file system during installation. If this script is supposed to run during application uninstallation, you should specify Destination; otherwise, the script will not reside on the local file system, and will not be able to run during uninstallation. If the path includes spaces, you must enclose it in double quotation marks (").|  
|**/Server** (or **/Se**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/Da**, see Remarks)|No|Name of the BizTalk Management database. If not provided, the BizTalk Management database running in the local instance of SQL Server is used.|  
|**/Property** (or **/P**, see Remarks)|No|Zero or more resource properties that will be passed to the script as arguments when the script is invoked.|  
  
## Sample  
 **BTSTask AddResource /ApplicationName:MyApplication /Type: System.BizTalk:PostProcessingScript /Overwrite /Source:"C:\Source Scripts\MyScript.vbs" /Destination:"C:\New Scripts\MyScript.vbs" /Server:MyDatabaseServer /Database:BizTalkMgmtDb /Property:Args="argument1 argument2"**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
 The following extensions are supported for script files: .com, .exe, .bat, .cmd, .vbs, .vbe, .js, .jse, .wsf, .wsh.  
  
## See Also  
 [AddResource Command](../core/addresource-command.md)   
 [How to Add a Pre- or Post-processing Script to an Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)