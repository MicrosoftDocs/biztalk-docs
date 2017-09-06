---
title: "ExportSettings Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa34dab1-c854-473e-a693-43ba45624e16
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ExportSettings Command
The ExportSettings command nables you to export the BizTalk Server settings from a BizTalk Server configuration database to an XML file. You can then import these settings in another environment as described in [How to Import BizTalk Settings Using Settings Dashboard](../core/how-to-import-biztalk-settings-using-settings-dashboard.md) or [How to Import BizTalk Settings Using BTSTask](../core/how-to-import-biztalk-settings-using-btstask.md).  
  
## Prerequisites  
 To perform this operation, you must be logged on as a member of the BizTalk Server Administrators group.  
  
## Usage  
 `ExportSettings –Destination:value[-Server:value] [-Database:value]`  
  
## Parameters  
  
|**Parameter**|Required|Value|  
|-------------------|--------------|-----------|  
|**-Destination**|Yes|Path and file name of the XML file to write.|  
|**-Server**|Optional|The name of SQL Server hosting the BizTalk configuration database.|  
|**-Database**|Optional|The name of the BizTalk configuration database.|  
  
## Sample  
 `BTSTask ExportSettings /Destination:MyFile.xml /Server:MyServer /Database:MyMgmtDb`  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)