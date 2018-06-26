---
title: "ImportBindings Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b8dd1ee-1719-4cd1-b503-b004f312daeb
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ImportBindings Command
Imports bindings from an XML-based binding file into a BizTalk application or group. The bindings may have been exported from an assembly, application, or group, as described in [Exporting Bindings](../core/exporting-bindings6.md). Depending on the location from which the bindings were exported, the ApplicationName and GroupLevel parameters have different effects. For more information, see "Remarks," later in this topic.  
  
> [!NOTE]
>  Binding files generated in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] do not have an application specified. They are imported into the default application.  
  
## Usage  
 **BTSTask ImportBindings -Source**:*value* [**-GroupLevel** &#124; **-ApplicationName**:*value*] [**-Server**:*value*] [**-Database**:*value*] [**-ImportTrackingSettings**:*value*] [**-ExcludeParties**]
  
## Parameters  
  
|                   Parameter                   | Required |                                                                                                                                                                                                                                                         Value                                                                                                                                                                                                                                                          |
|-----------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **-Source** (or **-So**, see Remarks)     | Required |                                                                                                                                                                                          Full path of the binding file to import, including the file name. Paths that include spaces must be enclosed in quotation marks (").                                                                                                                                                                                          |
|   **-GroupLevel** (or **-G**, see Remarks)    | Optional |                                                                                                                                                                                               Option to import the binding file into the current group. If you specify this parameter, do not specify /ApplicationName.                                                                                                                                                                                                |
| **-ApplicationName** (or **-A**, see Remarks) | Optional |                                                                          Name of the BizTalk application into which the bindings are to be imported. If the name includes spaces, you must enclose it with double quotation marks ("). The application must exist or the import operation will fail. If this parameter is not specified, the default BizTalk application is used. If you specify this parameter, do not specify /GroupLevel.                                                                           |
|     **-Server** (or **-Se**, see Remarks)     | Optional | Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used. |
|    **-Database** (or **-D**, see Remarks)     | Optional |                                                                                                                                                                                    Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.                                                                                                                                                                                     |
|          **-ImportTrackingSettings**          | Optional |                                                                                                                                           New starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. <br /><br />This overrides global tracking setting import option. A "true" value allows import of tracking settings. False disallows tracking setting import.                                                                                                                                           |
|              **-ExcludeParties**              | Optional |                                                                                                                                                                                 New starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. <br /><br />If specified, it excludes parties information from the binding file.                                                                                                                                                                                  |
  
## Sample  
 The following command imports bindings into the application named MyApplication in the default BizTalk group.  
  
`BTSTask ImportBindings -ApplicationName:MyApplication -Source:C:\Bindings\Binding1.xml`
  
 The following command imports bindings into the group defined in the BizTalk Management database running on a SQL Server instance named MY_Server.  
  
 `BTSTask ImportBindings -GroupLevel -Server:MY_Server -Database:BiztalkMgmtDb -Source:C:\Bindings\Binding1.xml`
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
 The bindings may have been exported from an assembly, application, or group. Depending on from where the bindings were exported, the ApplicationName and GroupLevel parameters have different effects, as shown in the following table.  
  
|Origin of the bindings|Effect with the ApplicationName parameter|Effect with the GroupLevel parameter|  
|----------------------------|-----------------------------------------------|------------------------------------------|  
|Bindings exported from an assembly|The application specified in ApplicationName must contain an assembly having the same name as the assembly from which the binding file was exported. Otherwise, the import operation fails.|The current group must contain an assembly and an application having the same name as the assembly and application from which the binding file was exported. Otherwise, the import fails.|  
|Bindings exported from an application|The application from which the binding file was exported must have the same name as the application specified by ApplicationName. Otherwise, the import operation fails.|The application from which the binding file was exported must have the same name as an application in the group into which you are importing the bindings. Otherwise, the import operation fails.|  
|Bindings exported from a group|The group from which the binding file was exported must include an application that has the same name as the application specified by ApplicationName. Otherwise, the import operation fails.|Bindings are imported for corresponding applications. In other words, the bindings of an application in the group from which bindings were exported are imported into an application having the same name in the current group.|  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)   
 [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md)   
 [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md)