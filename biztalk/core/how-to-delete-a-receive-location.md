---
title: "How to Delete a Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [receive locations], deleting"
  - "receive locations, deleting"
  - "deleting, receive locations"
ms.assetid: aa859355-af4c-48d9-b224-78fd3ef618fc
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Delete a Receive Location
This topic describes how to use the BizTalk Server Administration console to delete a receive location. When you delete a receive location, it is removed from the BizTalk Management database and is no longer displayed in the BizTalk Server Administration console.  
  
 When deleting a receive location, bear in mind the following important points:  
  
-   Before you can delete a receive location, it must first be disabled, as described in [How to Disable a Receive Location](../core/how-to-disable-a-receive-location.md).  
  
-   You cannot delete the primary receive location for a receive port. If you attempt this, you will receive an error message. To delete the receive location, you can either delete the receive port, which also deletes all of the receive locations that it contains, or you can make a different receive location primary and then delete the original receive location. For instructions on making a receive location the primary receive location, see [How to Edit the Properties of a Receive Location](../core/how-to-edit-the-properties-of-a-receive-location.md).  
  
-   After you delete a receive location, restart the Isolated Host Worker Processes corresponding to the deleted receive location.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To delete a receive location  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to delete a receive location.  
  
3. Click **Receive Locations**, right-click the receive location to delete, and then click **Delete**.  
  
## See Also  
 [Managing Receive Locations](../core/managing-receive-locations.md)