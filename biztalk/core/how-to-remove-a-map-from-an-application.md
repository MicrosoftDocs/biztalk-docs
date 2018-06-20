---
title: "How to Remove a Map from an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications, maps"
  - "deleting, maps"
  - "managing [maps], deleting"
  - "managing [maps], applications"
ms.assetid: 27d9bb08-36f0-46ff-ae9a-2247be6e3f96
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove a Map from an Application
This topic describes how to use the BizTalk Server Administration console to remove a map from a BizTalk application. You might want to remove a map after deploying a new version of the map. For more information and important considerations for updating application artifacts, see [Updating BizTalk Applications](../core/updating-biztalk-applications.md).  
  
 When you remove a map, the following occurs:  
  
-   The map is deleted from the BizTalk Management database.  
  
-   The BizTalk assembly that contains the map is deleted from the BizTalk Management database, but is not removed from the local file system or the global assembly cache (GAC), if it exists in these locations.  
  
-   As a consequence of the BizTalk assembly being deleted, all artifacts contained in the assembly are removed deleted the BizTalk Management database as well.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To remove a map  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the map to remove, and then expand the application containing the map.  
  
3. Click the **Maps** folder, right-click the map, and then click **Remove**.  
  
> [!NOTE]
>  To remove multiple maps, hold down the shift key, click each map to remove, right-click one of the maps, and then click **Remove**.  
  
## See Also  
 [Managing Maps](../core/managing-maps.md)   
 [How to Remove a BizTalk Assembly from an Application](../core/how-to-remove-a-biztalk-assembly-from-an-application.md)   
 [Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md)