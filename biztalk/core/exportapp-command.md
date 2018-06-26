---
title: "ExportApp Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6217d0f1-cf39-4520-87c8-8d25b21865af
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ExportApp Command
Exports a BizTalk application to an .msi file. If an .msi file having the same file name and path already exists, the existing .msi file is overwritten.  
  
 You can use the ResourceSpec parameter to selectively export the artifacts in an application to an .msi file. You specify which artifacts to export by editing the XML file created when you run the **ListApp** command with the ResourceSpec parameter, as described in [ListApp Command](../core/listapp-command.md). You then use the location of this XML file as the value of ResourceSpec when running the **ExportApp** command. When you do this, only the artifacts listed in the specified XML file are exported to the .msi file.  
  
> [!NOTE]
>  For security reasons, during application export, passwords are removed from application bindings. They are not removed from any binding files that have been added to the application. After installing the application from the .msi file, you must reconfigure the passwords in order for the application to function.  
>   
>  In addition, private keys are removed from certificate files.  
  
## Usage  
 **BTSTask ExportApp** [**/ApplicationName:**<em>value</em>] **/Package:**<em>value</em> [**/ResourceSpec:**<em>value</em>] [**/GlobalParties**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Value|  
|---------------|--------------|-----------|  
|**/ApplicationName** (or **/A**, see Remarks)|No|Name of the BizTalk application to export. If the name includes spaces, you must enclose it with double quotation marks ("). If the application name is not specified, the default BizTalk application for the group is used.|  
|**/Package** (or **/P**,see Remarks)|Yes|Full path of the .msi file. If the path includes spaces, you must enclose it in quotation marks ("). Example: Package:"C:\My MSI Files\My.msi"|  
|**/ResourceSpec** (or **/R**, see Remarks)|No|Full path of the resource specification file. If the path includes spaces, you must enclose it in quotation marks ("). Example: ResourceSpec:"C:\My Files\MyResourceSpec.xml"|  
|**/GlobalParties** (or **/G**, see Remarks)|No|If specified, global party information for the group is exported in the .msi file.|  
|**/Server** (or **/S**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/D**, see Remarks)|No|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **ExportApp /ApplicationName:MyApplication /Package:C:\MSI\MyApplication.msi**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)   
 [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md)