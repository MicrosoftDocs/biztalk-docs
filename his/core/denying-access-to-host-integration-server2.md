---
description: "Learn more about: Denying Access to Host Integration Server"
title: "Denying Access to Host Integration Server2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42590b2e-b0d1-4bb0-b43b-8969d8a0a410
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Denying Access to Host Integration Server
You can use one of two methods to deny a user or group the ability to use Host Integration Server. Either remove the user or group from the list of those who have permissions, or assign No Access to the user or group.  
  
 When removing a user or group from the list of those who have been granted permissions, be sure to consider all groups to which a particular user belongs. To deny access to that user, either remove the applicable groups from the list of those with permissions, or remove the user account from these groups. Otherwise, the user can receive access through one of the groups (unless the second method, assigning No Access, is used).  
  
 You can deny all access to a user or group by assigning No Access, which overrides any other permissions that may apply to a user. For example, if a user belongs to a group that has Read permission, but the user has No Access, the user is not permitted administrative access. Likewise, if a user belongs to Group1 and Group2, and Group1 has Read permission while Group2 has No Access, the user is not permitted administrative access.  
  
 The following table provides recommendations for using the two methods of denying access.  
  
|Method of denying access|Recommended situations for use|  
|------------------------------|------------------------------------|  
|Remove from list of those granted permissions|Use when you want to deny access to a medium or large group. If you then want to grant access to specific users in that group, add those users to the list of those with permissions.<br /><br /> In contrast, if you assign No Access to a large group, none of the members of the group will be allowed access, even if explicit access is assigned to them through other accounts.|  
|Assign No Access|Use when you want to deny access to an individual user or a small group. If you then want to grant access to other groups to which the affected users belong, you can do so. The No Access permission overrides the other permissions for the affected users.<br /><br /> In contrast, if you attempt to deny an individual user access by removing the user from the list of those granted permissions, a group to which the user belongs might be left in the list. The permissions assigned to that group would be given to the user.|  
  
## See Also  
 [Understanding Windows Security](../core/understanding-windows-security1.md)
