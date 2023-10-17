---
description: "Learn more about: Disabling BAM Tracking"
title: "Disabling BAM Tracking"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
