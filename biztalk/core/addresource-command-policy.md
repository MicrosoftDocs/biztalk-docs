---
title: "AddResource Command: Policy | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5effcbe-bf53-4741-8d5e-227620d4d84d
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AddResource Command: Policy
To add a policy to a BizTalk application, you use the **AddResource** command and specify **System.BizTalk:Rules** for the Type parameter. Running this command adds the policy to the BizTalk Management database. The policy is also displayed in the BizTalk Server Administration console, in the Policies folder of the application to which you added it. In addition, the policy is listed when you use the [ListApp Command](../core/listapp-command.md).  
  
 For this command to succeed, the policy must exist in the Rule Engine database. For instructions on importing a policy into the Rule Engine database, see [How to Import a Policy](../core/how-to-import-a-policy.md). When you add a policy by using AddResource command, any vocabularies used by the policy are automatically added as well.  
  
## Usage  
 **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:Rules** [**/Overwrite**] **/Name:**<em>value</em>**/Version:**<em>value</em> [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Value|  
|---------------|--------------|-----------|  
|**/ApplicationName** (or **/A**, see Remarks)|No|Name of the BizTalk application to which to add the policy. If the name includes spaces, you must enclose it in double quotation marks ("). If the application name is not specified, the default BizTalk application for the group is used.|  
|**/Type** (or **/T**, see Remarks)|Yes|**System.BizTalk:Rules** (This value is not case-sensitive.)|  
|**/Overwrite** (or **/O**, see Remarks)|No|Option to update an existing policy. If not specified, and a policy already exists in the application that has the same name as the policy being added, the AddResource operation fails.|  
|**/Name** (or **/N**, see Remarks)|Yes|Name of the policy.|  
|**/Version** (or **/V**, see Remarks)|Yes|Version number of the policy in the form number.number.<br /><br /> Example: 1.0|  
|**/Server** (or **/S**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/D**, see Remarks)|No|Name of the BizTalk Management database. If not provided, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **BTSTask AddResource /ApplicationName:MyApplication /Type: System.BizTalk:Rules  /Overwrite /Name:MyPolicy /Version:1.0 /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## Remarks  
 If MyPolicy has been deployed, the above command will return the following:  
  
 Error: Failed to add resource(s).  
  
 Validation failed for 1 resource(s).  
  
 Rules policy "MyPolicy" version 1.0 cannot be overwritten since is already in production.  
  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [AddResource Command](../core/addresource-command.md)   
 [How to Add a Policy to an Application](../core/how-to-add-a-policy-to-an-application.md)