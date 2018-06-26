---
title: "RemoveApp Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 323290ae-8498-4ad6-9b06-a1d54640250e
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# RemoveApp Command
Removes (deletes) from the BizTalk Management database a BizTalk application as well as all of the artifacts it contains. This does not uninstall the application. For instructions on doing this, see [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md).  
  
 The remove operation will fail in the following cases:  
  
- **The application is not stopped.** For instructions on stopping an application, see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md). The **ApplicationManager** SDK sample which is installed in the <em>\<Samples Path\>\\</em>Admin\ExplorerOM\ directory illustrates how to programmatically start or stop a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.  
  
- **Other applications contain references to the application.** If other applications contain references to the application you want to remove, you must first remove the references from the other applications. For instructions, see [How to Remove a Reference to Another Application](../core/how-to-remove-a-reference-to-another-application.md).  
  
- **The application contains a send port group of which a send port in another application is a member.** You must unenlist the member send port before you can delete the application. For instructions, see [How to Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md).  
  
- **The application contains a send port that is referenced by a party.** You can delete the reference from the party or move the send port to a different application. For instructions on performing these tasks, see [How to View or Edit a Party](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca) or [How to Move an Artifact to a Different Application](../core/how-to-move-an-artifact-to-a-different-application.md).  
  
- **The application is the default application.** If you want to delete it, you must first make another application the default. For instructions, see [How to Change the Default Application](../core/how-to-change-the-default-application.md).  
  
- **An orchestration in the application is enlisted, started, or has a suspended instance.** For more information about orchestrations, see [Managing Orchestrations](../core/managing-orchestrations.md).  
  
> [!NOTE]
>  If the application contains a policy that is in a deployed state, the policy is not removed from the Rule Engine database and continues to display in the Policies folder under the \<All Artifacts\> application node of the BizTalk Administration console. If you add the policy to another application, the policy remains in a deployed state.  
  
## Usage  
 **BTSTask RemoveApp /ApplicationName:** *value* [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Description|  
|---------------|--------------|-----------------|  
|**/ApplicationName** (or **/A**, see Remarks)|Yes|Name of the BizTalk application to delete. If the name includes spaces, you must enclose it with double quotation marks (").|  
|**/Server** (or **/S**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/D**, see Remarks)|No|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **BTSTask RemoveApp /ApplicationName:MyApplication**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)   
 [Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md)