---
description: "Learn more about: How to Create a Tracking Profile"
title: "How to Create a Tracking Profile | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tracking profiles, creating"
  - "creating, tracking profiles"
ms.assetid: 676ae7e8-f3eb-45f1-ad2e-807b434c0bf9
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Tracking Profile
You create tracking profiles to link BAM activity definitions to deployed assemblies and BizTalk Server messaging properties. When you open the Tracking Profile Editor, you can create a new tracking profile by either clicking the import activity link or the import menu item.  
  
## Prerequisites  
 The following are prerequisites for performing the procedure in this topic:  
  
-   An existing BizTalk Management database to which you have permissions.  
  
-   The TPE configured to use the BizTalk Management database.  
  
-   An existing BAM activity definition in the BAM Primary Import database.  
  
### To create a tracking profile  
  
1.  On the computer or computers that you have identified as the source system, open the **Tracking Profile Editor**. To do this, click **Start**, click **Run**, type **BTSTrkEditor.exe**, and then click **OK**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2.  In the middle of the left pane of the TPE, click **Click here to import a BAM Activity Definition** link. This opens the **Import BAM Activity Definition** dialog box.  
  
3.  From the **BAM Activity Definition Name** list box select the activity on which to base the tracking. If your list contains many deployed activities, you can type part of the activity name in the **In String** text box and click the **Search** button. This limits the list of activities displayed to those whose names contain the partial name entered.  
  
4.  Once you have selected the activity, click the **OK** button. This opens a new tracking profile based on the activity selected and displays the profile in the left pane of the TPE.  
  
## See Also  
 [Creating Tracking Profiles](../core/creating-tracking-profiles.md)
