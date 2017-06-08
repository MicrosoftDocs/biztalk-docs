---
title: "BizTalk Server Cross Reference Import Tool (BTSXRefImport.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BizTalk Server Cross Reference Import tool"
ms.assetid: d87a26b7-753b-4605-939a-0dd99c2a50d8
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Server Cross Reference Import Tool (BTSXRefImport.exe)
The BizTalk Server Cross Reference Import tool reads data from a series of XML files and stores the information in SQL Server tables.  
  
## Syntax  
  
```  
  
btsxrefimport  –file=setupfile  
```  
  
|Argument|Description|  
|--------------|-----------------|  
|*Setupfile*|An XML document file in the format described in [SetUp-Files Document](../core/setup-files-document.md) containing the names of the data files.|  
  
## Remarks  
 The import tool does not create the SQL Server tables. Rather, the BizTalk Server Configuration Wizard automatically creates the required tables during installation. For more information about the configuration wizard, see [Working with the Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md).  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## Example  
 In the following command, btsxrefimport reads the names of the data files from the XML document in the file `setupfile.xml`:  
  
```  
btsxrefimport –file=setupfile.xml  
```  
  
## See Also  
 [SetUp-Files Document](../core/setup-files-document.md)   
 [Importing Data for the Cross Referencing Functoids](../core/importing-data-for-the-cross-referencing-functoids.md)