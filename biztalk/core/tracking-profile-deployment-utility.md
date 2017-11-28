---
title: "Tracking Profile Deployment Utility | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d631b7c-a40f-4cee-88a4-3d932ab7fde0
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tracking Profile Deployment Utility
Developers use the bttdeploy utility to apply tracking profiles to and remove them from the BAM infrastructure. Using the bttdeploy utility is functionally equivalent to clicking the Apply Tracking Profile menu option in the Tracking Profile Editor (TPE).  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
 **Usage**  
  
 **bttdeploy.exe [options] file name**  
  
|Option|Description|  
|------------|-----------------|  
|/h or /?|Optional: Displays the syntax summary for bttdeploy.|  
|/mgdb \<server name[,port]\>\\<database name\>|Optional: Specifies the management server, port, and database name to which to apply the profile. **Note:**  When using this parameter, the port is optional.|  
|/remove|Optional: Specifies that the tracking profile is to be removed from the BAM database.|  
|filename|The name of the tracking profile file to apply or remove.|  
  
## See Also  
 [Tracking Profile Editor](../core/tracking-profile-editor.md)   
 [How to Remove Orphaned Tracking Profiles](../core/how-to-remove-orphaned-tracking-profiles.md)