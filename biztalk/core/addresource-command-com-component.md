---
description: "Learn more about: AddResource Command: COM Component"
title: "AddResource Command: COM Component"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# AddResource Command: COM Component
To add an unmanaged COM component to a BizTalk application, you use the **AddResource** command and specify **System.BizTalk:Com** for the Type parameter. Running this command adds the COM component to the BizTalk Management database. The COM component is also displayed in the BizTalk Administration console, in the Resources folder of the application to which you added it. In addition, the component is listed when you use the [ListApp Command](../core/listapp-command.md).  
  
> [!NOTE]
>  If you add a 64-bit unmanaged COM or COM+ component, and you attempt to install the application that includes the COM or COM+ component on a 32-bit computer, the component will not be installed. It will install only on a 64-bit computer.  
  
## Usage  
 **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:Com** [**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Options:Regsvr32OnInstall**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Value|  
|---------------|--------------|-----------|  
|**/ApplicationName** (or **/A**, see Remarks)|No|Name of the BizTalk application to which to add the COM component. If the name includes spaces, you must enclose it in double quotation marks ("). If the application name is not specified, the default BizTalk application for the group is used.|  
|**/Type** (or **/T**, see Remarks)|Yes|**System.BizTalk:Com** (This value is not case-sensitive.)|  
|**/Overwrite** (or **/Ov**, see Remarks)|No|Option to update an existing COM component. If not specified, and a COM component already exists in the application that has the same file name as the COM component being added, the AddResource operation fails.|  
|**/Source** (or **/So**, see Remarks)|Yes|Full path of the COM component .dll file, including the file name. If the path includes spaces, you must enclose it in double quotation marks (").|  
|**/Destination** (or **/De**, see Remarks)|No|Full path of the location where the COM component .dll file is to be copied when the application is installed from the .msi file. If not provided, the file is not copied to the local file system during installation; therefore, the component cannot be added to the Windows registry during installation. If the path includes spaces, you must enclose it in double quotation marks ("). If you specify the Regsvr32OnInstallOption, you must also specify Destination.|  
|**/Options** (or **/Op**, see Remarks)|No|**Regsvr32OnInstall.** Specify to add the COM component to the Windows registry when the application is installed from the .msi file. If you specify this option, you must also specify Destination.|  
|**/Server** (or **/Se**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/Da**, see Remarks)|No|Name of the BizTalk Management database. If not provided, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **BTSTask AddResource /ApplicationName:MyApplication /Type: System.BizTalk:Com  /Overwrite /Source:"C:\Source Components\COM.dll" /Destination:"C:\New Components\COM.dll" /Options:Regsvr32OnInstall /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [AddResource Command](../core/addresource-command.md)   
 [How to Add a .NET Assembly to an Application](../core/how-to-add-a-net-assembly-to-an-application.md)
