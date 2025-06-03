---
description: "Learn more about: Deploying Localized BAM XML Files"
title: "Deploying Localized BAM XML Files"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Deploying Localized BAM XML Files
Microsoft SQL Server Analysis Services supports Unicode mapping. However, there are known character corruption issues with SQL Server Analysis Services and Visual Basic Unicode mapping. Specifically, if the regional settings are not set to the correct localized language when the conversion from ANSI to Unicode occurs, the conversion is performed using the wrong locale information and character corruption occurs.  
  
 To deploy the BAM definition XML file successfully, you must switch your system locale to the correct locale before you can actually deploy a BAM definition XML file that contains localized characters.  
  
## See Also  
 [Managing BAM](../core/managing-bam.md)   
 [BAM Management Utility](../core/bam-management-utility.md)
