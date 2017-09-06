---
title: "ImportSettings Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 587f7e1f-9cf7-4e7b-90cd-11a266f474dc
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ImportSettings Command
Imports the BizTalk group, host, or host instance settings from a source XML file to the configuration database. The settings are mapped as they are in the mapping XML file. These settings may have been exported as described in [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) or [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md).  
  
## Prerequisites  
 To perform this operation, you must be signed in as a member of the BizTalk Server Administrators group.  
  
## Usage  
 `ImportSettings –Source:value –Map: value [-Server:value] [-Database:value]`  
  
## Parameters  
  
|**Parameter**|Required|Value|  
|-------------------|--------------|-----------|  
|**-Source**|Yes|Path and file name of the exported settings XML file.|  
|**-Map**|Yes|Path and file name of the mapping XML file.|  
|**-Server**|Optional|The name of SQL Server computer hosting the BizTalk configuration database.|  
|**-Database**|Optional|The name of the BizTalk configuration database.|  
  
## Sample  
 `BTSTask ImportSettings /Source:”C:\My Folder>\ExportedSettings.xml” /Map:Mappings.xml /Server:MyServer /Database:MyMgmtDb`  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)