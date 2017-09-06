---
title: "Release Phase Recommendations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5ac72aa-decd-4b3e-be34-e585e54568b3
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Release Phase Recommendations
The release phase involves propagating the now validated system onto the production hardware.  
  
## Propagate Test Bed Optimizations to Production Systems  
 Propagating the system artifacts and configuration onto the production hardware and starting it up to process is a relatively straightforward process. However, in practice, there are things to consider regarding performance during this phase that can be easily missed:  
  
-   **Verify that platform optimizations are propagated**. During implementation and verification, it is common to implement any number of platform level performance optimizations.  
  
     For example, when using an isolated adapter such as HTTP on Internet Information Server (IIS), there are a number of common performance optimizations that can be used such as increasing the number of processes in IIS in which the adapters will run. Any such performance optimizations found before release must be tracked and propagated to the production environment as well.  
  
-   **Set up and automate data backup, log shipping, data retention configurations, and purging tasks**. As part of certification for production, the frequency at which databases are backed up and purged (for example, the BizTalk Tracking database and BAM database) is key to sustainability so those settings must be migrated to production they don’t already exist there.  
  
## See Also  
 [Project Planning Recommendations by Phase](../core/project-planning-recommendations-by-phase.md)   
 [Requirements Phase Recommendations](../core/requirements-phase-recommendations.md)   
 [Design Phase Recommendations](../core/design-phase-recommendations.md)   
 [Implementation Phase Recommendations](../core/implementation-phase-recommendations.md)   
 [Verification Phase Recommendations](../core/verification-phase-recommendations.md)