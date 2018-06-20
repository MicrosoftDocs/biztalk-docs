---
title: "AddResource Command: File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9635e43-af26-48d3-af0e-df245a8955e7
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AddResource Command: File
To add a file to a BizTalk application, you use the **AddResource** command and specify **System.BizTalk:File** for the Type parameter. Running this command adds the file to the BizTalk Management database. The file is also displayed in the BizTalk Administration console, in the Resources folder of the application to which you added it. In addition, the file is listed when you use the [ListApp Command](../core/listapp-command.md).  
  
## Usage  
 **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:File** [**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Value|  
|---------------|--------------|-----------|  
|**/ApplicationName** (or **/A**, see Remarks)|No|Name of the BizTalk application to which to add the file. If the path includes spaces, you must enclose it in double quotation marks ("). If the application name is not specified, the default BizTalk application is used.|  
|**/Type** (or **/T**, see Remarks)|Yes|**System.BizTalk:File** (This value is not case-sensitive.)|  
|**/Overwrite** (or **/O**, see Remarks)|No|Option to update an existing file. If not specified, and a file already exists in the application that has the same name as the file being added, the AddResource operation fails.|  
|**/Source** (or **/So**, see Remarks)|Yes|Full path of the file, including the file name. If the path includes spaces, you must enclose it in double quotation marks (").|  
|**/Destination** (or **De**, see Remarks)|No|Full path of the location where the file is to be copied when the application is installed from the .msi file. If the path includes spaces, you must enclose it in double quotation marks ("). If not provided, the file is not copied to the local file system during installation.|  
|**/Server** (or **/Se**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/Da**, see Remarks)|No|Name of the BizTalk Management database. If not provided, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **BTSTask AddResource /ApplicationName:MyApplication /Type: System.BizTalk:File   /Overwrite /Source:"C:\Source Files\File.txt" /Destination:"C:\New Files\File.txt" /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [AddResource Command](../core/addresource-command.md)   
 [How to Add a .NET Assembly to an Application](../core/how-to-add-a-net-assembly-to-an-application.md)