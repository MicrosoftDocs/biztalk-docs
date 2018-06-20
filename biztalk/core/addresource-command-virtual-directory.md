---
title: "AddResource Command: Virtual Directory | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 446be3b3-31da-4f03-81b5-3a75c8da6558
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AddResource Command: Virtual Directory
To add a virtual directory for a Web site or Web services to a BizTalk application, you use the **AddResource** command and specify **System.BizTalk:WebDirectory** for the Type parameter. Running this command adds the virtual directory to the BizTalk Management database. The virtual directory is also displayed in the BizTalk Server Administration console, in the Resources folder of the application to which you added it. In addition, the virtual directory is listed when you use the [ListApp Command](../core/listapp-command.md).  
  
> [!IMPORTANT]
>  When you add a virtual directory with a URL that contains https, you must use http in the URL that you specify rather than https. If you use https, the operation to add a virtual directory will fail. Even though you add it with http in the URL, the https setting for the URL in the Internet Information Services metabase will be in effect, and the virtual directory will function correctly.  
  
> [!NOTE]
>  If you add a virtual directory from a 64-bit version of the Web service, and you attempt to install the application that includes the virtual directory on a 32-bit computer, the virtual directory will not be installed. It will  install only on a 64-bit computer.  
  
## Usage  
 **BTSTask AddResource** [/**ApplicationName:**<em>value</em>] **/Type:System.BizTalk:WebDirectory**[**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|                   Parameter                   | Required |                                                                                                                                                                                                                                                         Value                                                                                                                                                                                                                                                          |
|-----------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **/ApplicationName** (or **/A**, see Remarks) |    No    |                                                                                                                                Name of the BizTalk application to which to add the virtual directory. If the name includes spaces, you must enclose it in double quotation marks ("). If the application name is not specified, the default BizTalk application for the group is used.                                                                                                                                 |
|      **/Type** (or **/T**, see Remarks)       |   Yes    |                                                                                                                                                                                                                          **System.BizTalk:WebDirectory** (This value is not case-sensitive.)                                                                                                                                                                                                                           |
|    **/Overwrite** (or **/O**, see Remarks)    |    No    |                                                                                                                                               Option to update an existing virtual directory. If not specified, and a virtual directory already exists in the application that has the same name as the virtual directory being added, the AddResource operation fails.                                                                                                                                                |
|     **/Source** (or **/S**, see Remarks)      |   Yes    |                                                                                                                                                                                                 Full URI of the source virtual directory.<br /><br /> Examples:<br /><br /> http://MyHost:80/MyPath/MyVirtualDirectory                                                                                                                                                                                                 |
|  **/Destination** (or **/De**, see Remarks)   |    No    |                                                                                                                                                    URI to be assigned to the virtual directory when the application is installed from the .msi file. If this parameter is not specified, then the value of the Source parameter is used with localhost as the host.                                                                                                                                                    |
|     **/Server** (or **/S**, see Remarks)      |    No    | Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used. |
|    **/Database** (or **/Da**, see Remarks)    |    No    |                                                                                                                                                                                     Name of the BizTalk Management database. If not provided, the BizTalk Management database running in the local instance of SQL Server is used.                                                                                                                                                                                     |
  
## Sample  
 **BTSTask AddResource /ApplicationName:MyApplication /Type: System.BizTalk:WebDirectory /Overwrite /Source:<http://Host1:90/MyVirtualDirectory> /Destination:<http://Host2:90/MyVirtualDirectory> /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [AddResource Command](../core/addresource-command.md)   
 [How to Add a .NET Assembly to an Application](../core/how-to-add-a-net-assembly-to-an-application.md)