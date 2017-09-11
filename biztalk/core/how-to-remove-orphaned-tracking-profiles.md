---
title: "How to Remove Orphaned Tracking Profiles | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deleting, tracking profiles"
  - "tracking profiles, orphans"
  - "tracking profiles, activities"
  - "tracking profiles, deleting"
  - "activities, tracking profiles"
ms.assetid: e8923dab-5d02-41a3-840b-104b20624e6c
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove Orphaned Tracking Profiles
Tracking profiles are associated with an activity. If an activity is undeployed, the associated tracking profiles can become orphaned, which means they are no longer associated with an activity. You can use the following procedure to remove the tracking profile.  
  
### To remove an orphaned tracking profile  
  
1.  Redeploy the BAM definition. For information about deploying BAM definitions, see [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md).  
  
2.  Use the Tracking Profile Editor (TPE) to remove the tracking profile. For information about removing tracking profiles, see [How to Apply and Remove a Tracking Profile](../core/how-to-apply-and-remove-a-tracking-profile.md).  
  
3.  Undeploy the BAM definition. For information about removing BAM definitions, see [How to Remove BAM Definitions](../core/how-to-remove-bam-definitions.md).  
  
## See Also  
 [Tracking Profile Editor](../core/tracking-profile-editor.md)   
 [BAM Management Utility](../core/bam-management-utility.md)