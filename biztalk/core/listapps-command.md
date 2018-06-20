---
title: "ListApps Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a5eb0af-e153-4639-a6c0-56c951827c7c
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ListApps Command
Prints to the console the name and description of all of the BizTalk applications in the specified BizTalk Management database.  
  
## Usage  
 **BTSTask ListApps** [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
## Parameters  
  
|Parameter|Required|Description|  
|---------------|--------------|-----------------|  
|**/Server** (or **/S**, see Remarks)|No|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
|**/Database** (or **/D**, see Remarks)|No|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## Sample  
 **BTSTask ListApps**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)