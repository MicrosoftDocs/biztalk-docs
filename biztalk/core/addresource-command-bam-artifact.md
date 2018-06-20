---
title: "AddResource Command: BAM Artifact | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9de7a82-9b06-4d50-9678-73140e80d0af
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AddResource Command: BAM Artifact
To add a BAM artifact to a BizTalk application, you use the **AddResource** command and specify **System.BizTalk:Bam** for the Type parameter. Running this command adds the BAM artifact file to the BizTalk Management database. The BAM artifact is also displayed in the BizTalk Server Administration console, in the Resources folder of the application to which you added it. In addition, the file is listed when you use the [ListApp Command](../core/listapp-command.md).  
  
 Adding a BAM definition by using the AddResource command does not deploy the BAM definition. When an .msi file that includes a BAM definition is imported into an application by using the Import Wizard, however, the BAM definition is deployed to the local computer.  
  
## Usage  
 **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:Bam**[**/Overwrite**] **/Source:**<em>value</em> [**/Destination:**<em>value</em>] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Value|  
|---------------|--------------|-----------|  
|**/ApplicationName** (or **/A**, see Remarks)|No|Name of the BizTalk application to which to add the BAM artifact. If the name includes spaces, you must enclose it in double quotation marks ("). If the application name is not specified, the default BizTalk application for the group is used.|  
|**/Type** (or **/T**, see Remarks)|Yes|**System.BizTalk:Bam** (This value is not case-sensitive.)|  
|**/Overwrite** (or **/O**, see Remarks)|No|Option to update an existing BAM artifact. If not specified, and an artifact already exists in the application that has the same name as the BAM artifact being added, the AddResource operation fails.|  
|**/Source** (or **/So**, see Remarks)|Yes|Full path of the BAM artifact file, including the file name. If the path includes spaces, you must enclose it in double quotation marks (").|  
|**/Destination** (or **De**, see Remarks)|No|Full path of the location where the BAM artifact file is to be copied when the application is installed from the .msi file. If not provided, the file is not copied to the local file system during installation. If the path includes spaces, you must enclose it in double quotation marks (").|  
|**/Server** (or **/Se**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/Da**, see Remarks)|No|Name of the BizTalk Management database. If not provided, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **BTSTask AddResource /ApplicationName:MyApplication /Type: System.BizTalk:Bam   /Overwrite /Source:"C:\Source BAMfiles\MyBAMfile.xml" /Destination:"C:\New BAMfiles\MyBAMfile.xml" /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [AddResource Command](../core/addresource-command.md)   
 [How to Add a BAM Artifact to an Application](../core/how-to-add-a-bam-artifact-to-an-application.md)