---
title: "Disabling BAM Tracking | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FIN Response Reconciliation, disabling BAM tracking"
  - "BAM tracking"
ms.assetid: ea5fef0e-7a96-46f5-81d8-9b1d8a5d24d2
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Disabling BAM Tracking
By default, BAM tracking is enabled for FIN Response Reconciliation. You can disable it as follows.  
  
### To disable BAM tracking for FRR  
  
1.  Click **Start**, click **Run**, type **regedit**, and then click **OK**.  
  
2.  In the left pane of the Registry Editor, move to My Computer/HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/BizTalk Accelerator for SWIFT/FRR.  
  
    > [!IMPORTANT]
    >  This registry entry must be modified on each computer that FIN Response Reconciliation is running on.  
  
3.  In the right pane of the Registry Editor, double-click **BAMTrackingEnabled**.  
  
4.  In the **Edit DWORD Value** dialog box, in the **Value data** box, type **0** to disable BAM tracking.  
  
5.  Click **OK**.