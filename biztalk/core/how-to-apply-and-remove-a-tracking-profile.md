---
title: "How to Apply and Remove a Tracking Profile | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deleting, tracking profiles"
  - "tracking profiles, testing"
  - "tracking profiles, deleting"
  - "testing, tracking profiles"
ms.assetid: 77cef14b-c390-4da7-a383-b3abe414a168
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Apply and Remove a Tracking Profile
Once you have created or modified the tracking profile, the next step is to apply it to a test database and verify the result through integration testing. You can apply the tracking profile from within Tracking Profile Editor (TPE) itself or by using the command line.  
  
## Prerequisites  
 A previously created tracking profile that you saved to your hard drive.  
  
### To apply the tracking profile from within the TPE  
  
1. Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Tracking Profile Editor**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2. On the **File** menu, click **Open**. Navigate to the correct .btt file on your hard drive. Click **Open** to load it.  
  
3. On the **Tools** menu, click **Apply Tracking Profile** to apply the .btt file to a management database that you have set from the **Set Management Database** menu item on the **Tools** menu. Verify the result through integration testing.  
  
4. Notify the person in your organization responsible for deployment that the tracking profile tests correctly and is ready for deployment.  
  
### To apply the tracking profile from the command line  
  
-   From the command prompt, run the bttdeploy.exe tool located in the \Tracking folder as follows:  
  
    ```  
    bttdeploy.exe <profile name>.btt  
    ```  
  
> [!NOTE]
>  You must have BizTalk Administrator privileges to use this tool.  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
> [!IMPORTANT]
>  During the deployment, bttdeploy verifies the assembly version contained in the tracking profiles and matches it to the version of the deployed assembly. Bttdeploy will fail if the assembly is not currently deployed.  
  
> [!IMPORTANT]
>  When applying a tracking profile from the command line, bttdeploy applies the profile to the BizTalk Management database that you indicated when you ran the configuration wizard. If you specify a different database setting in the Tracking Profile Editor Option "Set Management Database," then that setting is used. If you specify a management server and database as part of the command line option to bttdeploy, then the command line option overrides everything else. For more information about using bttdeploy, see [Tracking Profile Deployment Utility](../core/tracking-profile-deployment-utility.md).  
  
### To remove a tracking profile  
  
1. Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Tracking Profile Editor**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2. On the **File** menu, click **Open**. Navigate to the correct .btt file on your hard drive. Click **Open** to load it.  
  
3. On the **Tools** menu, click **Remove Tracking Profile** to remove the tracking profile based on the .btt file from the BizTalk Management database.  
  
## See Also  
 [Creating Tracking Profiles](../core/creating-tracking-profiles.md)