---
title: "How to Assign LUs to Configured Users2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b3fa206-5071-479a-a7f5-b734c5406c1c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Assign LUs to Configured Users
Although [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] uses the User accounts of the Windows Active Directory directory service, users must be configured to use Host Integration Server resources such as LUs.  
  
### To assign LUs to configured users  
  
1. In SNA Manager, expand the SNA subdomain where the users reside.  
  
2. Expand **Configured Users**. Select a user, and then right-click **Assign LUs**.  
  
3. Select an LU, and then click **OK**.  
  
   The list of LUs that a particular user can access depends on how the user connects to Host Integration Server. If Active Directory is used, a user can access any LUs assigned directly to the user account and can also access any LUs assigned to any of the groups the user is a member of. If not using Active Directory, a user can only access LUs assigned directly to the user, or if no LUs are assigned to the user account, then the user can access LUs assigned to exactly one group. The groups are checked in the following order: global groups, local groups, well known groups. There is no ordering within a group.  
  
## See Also  
 [IP-DLC Link Service](./ip-dlc-link-service2.md)   
 [How to Add New Users](../core/how-to-add-new-users1.md)   
 [How to Assign Remote APPC LUs to Configured Users](../core/how-to-assign-remote-appc-lus-to-configured-users1.md)   
 [Step 4 (A) Adding and Assigning Users](../core/step-4-a-adding-and-assigning-users1.md)