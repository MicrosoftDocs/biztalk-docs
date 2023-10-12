---
description: "Learn more about: AddApp Command"
title: "AddApp Command"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# AddApp Command
Creates a new BizTalk application in the BizTalk Management database. You can view the application in the Applications node of the BizTalk Server Administration console. You can add artifacts to the application by using the AddResource command, as described in [AddResource Command](../core/addresource-command.md).  
  
## Usage  
 **BTSTask AddApp /ApplicationName:** *value* [**/Description:**<em>value</em>] [**/Default**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Value|  
|---------------|--------------|-----------|  
|**/ApplicationName** (or **/A**, see Remarks)|Yes|Name of the BizTalk application to add. If the application name includes spaces, it must be enclosed in double quotation marks (").|  
|**/Default** (or **/Def**, see Remarks)|No|When specified, makes the new application the default application for the BizTalk group.|  
|**/Description** (or **/Des**, see Remarks)|No|Description of the application. Must be enclosed in double quotation marks (").|  
|**/Server** (or **/S**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/Da**, see Remarks)|No|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **AddApp /ApplicationName:MyApplication /Description:"My BizTalk application"**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)   
 [How to Create an Application](../core/how-to-create-an-application.md)
