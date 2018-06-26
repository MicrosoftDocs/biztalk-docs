---
title: "RemoveResource Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8e2c6046-43d4-4ac1-a1b1-3795b4e44038
caps.latest.revision: 29
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# RemoveResource Command
Removes (deletes) an artifact from the BizTalk Management database. Running this command does not remove the artifact from the global assembly cache (GAC), file system, certificate store, Internet Information Services, or the Windows registry, if it exists in any of these locations. It does not remove a BAM definition from the BAM Primary Import database nor does it remove policies from the Rule Engine database. If you run this command to remove a binding file, the bindings remain unchanged – only the binding file is removed.  
  
 You can use this command to remove the following artifact types:  
  
- .NET assembly (System.BizTalk:Assembly)  
  
- BAM definition (System.BizTalk:Bam)  
  
- BizTalk assembly (System.BizTalk:BizTalkAssembly  
  
- BizTalk binding file (System.BizTalk:BizTalkBinding)  
  
- Security certificate (System.BizTalk:Certificate)  
  
- COM component (System.BizTalk:Com)  
  
- Ad hoc file (System.BizTalk:File)  
  
- Postprocessing script (System.BizTalk:PostProcessingScript)  
  
- Preprocessing script (System.BizTalk:PreProcessingScript)  
  
- Policy or rule (System.BizTalk:Rules)  
  
- Virtual directory (System.BizTalk:WebDirectory)  
  
  The remove operation will fail in the following cases:  
  
- You attempt to remove a BizTalk assembly to which another assembly has a reference.  
  
- You attempt to remove a BizTalk assembly that includes a pipeline that is used by a send or receive port.  
  
- You attempt to remove a BizTalk assembly that includes a map used by a send port.  
  
- You attempt to remove a BizTalk assembly that includes an orchestration that is not in an unenlisted state or that has a suspended instance.  
  
## Usage  
 **BTSTask RemoveResource /ApplicationName:** *value* **/Luid:** *value* [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Description|  
|---------------|--------------|-----------------|  
|**/ApplicationName** (or **/A**, see Remarks)|Yes|Name of the BizTalk application containing the resource artifact to delete. If the name includes spaces, you must enclose it with double quotation marks (").|  
|**/Luid** (or **/L**, see Remarks)|Yes|Locally unique identifier (LUID) of the artifact. You can obtain the LUID by using the [ListApp Command](../core/listapp-command.md).|  
|**/Server** (or **/S**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/D**, see Remarks)|No|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)   
 [How to Remove an Artifact from an Application](../core/how-to-remove-an-artifact-from-an-application.md)