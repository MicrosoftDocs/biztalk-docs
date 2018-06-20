---
title: "How to List Changes to the BAM Infrastructure | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "definitions [BAM], listing infrastructure changes"
  - "managing [BAM definitions], listing infrastructure changes"
  - "Get-Changes command [BAM]"
  - "infrastructure, listing changes [BAM]"
ms.assetid: 3feacd7d-6f42-4626-835b-0dc3befc9fd6
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to List Changes to the BAM Infrastructure
Administrators use the **get-changes** command of the BAM Management utility to list current information about a deployed BAM definition. You can also use the get-changes command to list current deployment artifacts in the BAM Primary Import database.  
  
 The information includes successful deployments and undeployments, the name of the BAM definition file, the name of the BAM configuration file, the names of all activities and views associated with the definition file, and the user account that applied the change. The get-changes list shows deployments and definition removals with their associated identification numbers.  
  
### To list changes to the BAM definition  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type **bm get-changes.**  
  
4. Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Security Recommendations](../core/bam-security-recommendations.md)   
 [BAM Management Utility](../core/bam-management-utility.md)