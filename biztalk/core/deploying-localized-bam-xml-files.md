---
title: "Deploying Localized BAM XML Files | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAM, unicode mapping"
  - "unicode mapping [BAM]"
ms.assetid: 8e7e3431-cd20-45db-b7f2-0df23e9df42b
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploying Localized BAM XML Files
Microsoft SQL Server Analysis Services supports Unicode mapping. However, there are known character corruption issues with SQL Server Analysis Services and Visual Basic Unicode mapping. Specifically, if the regional settings are not set to the correct localized language when the conversion from ANSI to Unicode occurs, the conversion is performed using the wrong locale information and character corruption occurs.  
  
 To deploy the BAM definition XML file successfully, you must switch your system locale to the correct locale before you can actually deploy a BAM definition XML file that contains localized characters.  
  
## See Also  
 [Managing BAM](../core/managing-bam.md)   
 [BAM Management Utility](../core/bam-management-utility.md)