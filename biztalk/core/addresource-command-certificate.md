---
title: "AddResource Command: Certificate | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e915043-6634-4644-8d69-376d762c7cec
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AddResource Command: Certificate
To add a security certificate to a BizTalk application, you use the **AddResource** command and specify **System.BizTalk:Certificate** for the Type parameter. For this command to work, the certificate must be present in the Other People certificate store on the local computer.  
  
 Running this command adds the certificate to the BizTalk Management database. The certificate is also displayed in the BizTalk Server Administration console, in the Resources folder of the application to which you added it. In addition, the certificate is listed when you use the [ListApp Command](../core/listapp-command.md).  
  
 When you install the application, the certificate is imported into the Other People certificate store on the local computer.  
  
## Usage  
 **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:Certificate** [**/Overwrite**] **/Thumbprint:"**<em>value</em>**"** [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Value|  
|---------------|--------------|-----------|  
|**/ApplicationName** (or **/A**, see Remarks)|No|Name of the BizTalk application to which to add the certificate. If the name includes spaces, you must enclose it in double quotation marks ("). If the application name is not specified, the default BizTalk application for the group is used.|  
|**/Type** (or **/Ty**, see Remarks)|Yes|**System.BizTalk:Certificate** (This value is not case-sensitive.)|  
|**/Overwrite** (or **/O**, see Remarks)|No|Option to update an existing certificate. If not specified, and a certificate already exists in the application that has the same Thumbprint property as the certificate being added, the Add operation fails. You can view the Thumbprint property by double-clicking the certificate in the Certificates snap-in and clicking the Details tab. For more information, see "Viewing certificate information" in the documentation for the Certificates snap-in.|  
|**/Thumbprint** (or **/Th**, see Remarks)|Yes|Thumbprint property of the certificate (a *thumbprint* is a digest of data). This value must be enclosed in double quotation marks (").|  
|**/Server** (or **/S**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/D**, see Remarks)|No|Name of the BizTalk Management database. If not provided, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **BTSTask AddResource /ApplicationName:MyApplication /Type: System.BizTalk:Certificate  /Overwrite /Thumbprint:"04 a2 8e 32 24 f9 36 b9 42 81 12 71 3a d2 ef db c7 9c 83 dc" /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [AddResource Command](../core/addresource-command.md)   
 [How to Add a Certificate to an Application](../core/how-to-add-a-certificate-to-an-application.md)