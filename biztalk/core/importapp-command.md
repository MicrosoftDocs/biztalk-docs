---
title: "ImportApp Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8ee5a78-1e8f-4290-b70a-36f2f888a1d6
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ImportApp Command
Imports the artifacts contained in an .msi file into a BizTalk application. If the application does not already exist, it is created.  
  
 When you import an application, you can use the /Environment parameter to specify the target deployment environment for the application, if you have added binding files to this application that are customized for a particular deployment environment. For background information, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md). For instructions on adding binding files, see [AddResource Command: BizTalk Binding](../core/addresource-command-biztalk-binding.md).  
  
> [!NOTE]
>  An import operation will time out if it exceeds 3600 seconds in duration. If you are attempting to import an .msi file, and the operation times out, you should divide the contents of the application into more than one .msi file by re-exporting the application and selecting a subset of artifacts to export. For more information, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).  
  
 If the import fails, BTSTask returns displaying the number of errors. Most of the actions taken during the operation are rolled back, except the following:  
  
- Actions taken by custom scripts are not rolled back. You can write your scripts so that they roll back by using the Delete environment variable.  
  
- If assemblies were installed in the global assembly cache (GAC), they are not removed.  
  
- Entries make in the Windows registry are not removed.  
  
  If the import is successful, BTSTask returns "0".  
  
## Usage  
 **BTSTask ImportApp /Package:** *value* [**/Environment:**<em>value</em>] [**/ApplicationName:**<em>value</em>] [**/Overwrite**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Value|  
|---------------|--------------|-----------|  
|**/Package** (or **/P**, see Remarks)|Yes|Full path of the .msi file. If the path includes spaces, you must enclose it in double quotation marks ("). Example: "C:\My MSI Files\MyApplication.msi"|  
|**/Environment** (or **/E**, see Remarks)|No|The target deployment environment of the binding file to apply, such as Test. This is the value that was specified for the target deployment environment when the binding file was added to the application. When not specified, all bindings that do not have an environment specified are applied.|  
|**/ApplicationName** (or **/A**, see Remarks)|No|Name of the BizTalk application to which the artifacts in the .msi file are imported. If the name includes spaces, you must enclose it with double quotation marks ("). If not specified, the default application is used. If the specified application does not exist, the application is created.|  
|**/Overwrite** (or **/O**, see Remarks)|No|Option to overwrite artifacts in the application with artifacts in the .msi file that have the same locally unique identifier (LUID). You can view the LUIDs of the artifacts in an application by using the [ListApp Command](../core/listapp-command.md). If this option is not specified, and there are one or more artifacts in the application that have the same LUID as artifacts in the .msi file, the import fails.|  
|**/Server** (or **/S**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/D**, see Remarks)|No|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **BTSTask ImportApp /Package:C:\MSI\MyApplication.msi /Environment:Test /ApplicationName:MyApplication /Overwrite**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)   
 [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md)