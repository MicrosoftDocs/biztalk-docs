---
description: "Learn more about: How to Remove Deployed Artifacts"
title: "How to Remove Deployed Artifacts"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Remove Deployed Artifacts
Administrators use the **remove-all** command to remove artifacts deployed in the BAM Primary Import database. The supplied BAM definition is either an XML file or an Excel Workbook containing information about the artifacts to be removed.  
  
### To remove deployed artifacts  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type **bm remove-all -DefinitionFile:\<def file\>**.  
  
4. Press **ENTER**.  
  
## See Also  
 [How to Add a BAM Artifact to an Application](../core/how-to-add-a-bam-artifact-to-an-application.md)   
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Security Recommendations](../core/bam-security-recommendations.md)   
 [BAM Management Utility](../core/bam-management-utility.md)
