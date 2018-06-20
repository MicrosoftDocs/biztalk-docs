---
title: "ExportBindings Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6573142e-7ca7-4990-98e3-b7a54840da13
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ExportBindings Command
Exports bindings for a BizTalk assembly, application, or group. You can also export global party bindings along with the assembly, application, or group bindings. (A party is all the entities, such as partners of your organization, that interact with an orchestration.)  
  
## Usage  
 **BTSTask ExportBindings /Destination:** *value* [**/GroupLevel**] [**/ApplicationName:**<em>value</em>] [**/AssemblyName:**<em>value</em> ] &#124; [**/GlobalParties**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Value|  
|---------------|--------------|-----------|  
|**/Destination** (or **/De**, see Remarks)|Yes|Full path of the binding file to create, including the file name. If a binding file having the same path already exists, it is overwritten. If the path includes spaces, you must enclose it in double quotation marks (").|  
|**/GroupLevel** (or **/Gr**, see Remarks)|No|When specified, all bindings in the current group are exported. You can specify only one of these three parameters: GroupLevel, ApplicationName, or AssemblyName.|  
|**/ApplicationName** (or **/Ap**, see Remarks)|No|Name of the application from which to export bindings. The application must exist. If the name includes spaces, you must enclose it with double quotation marks ("). To verify the application name, you can use the **ListApps** command, as described in [ListApps Command](../core/listapps-command.md). If this parameter is not specified, the default BizTalk application is used. You can specify only one of these three parameters: GroupLevel, ApplicationName, or AssemblyName.|  
|**/AssemblyName** (or **/As**, see Remarks)|No|Locally unique identifier (LUID) of the assembly from which to export bindings. You can view the list of LUIDs for the artifacts in an application by using the [ListApp Command](../core/listapp-command.md). You can specify only one of these three parameters: GroupLevel, ApplicationName, or AssemblyName.|  
|**/GlobalParties** (or **/Gl**, see Remarks)|No|When specified, exports the global party information for the group.|  
|**/Server** (or **/S**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/Da**, see Remarks)|No|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml" /GroupLevel /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)   
 [Exporting Bindings](../core/exporting-bindings6.md)