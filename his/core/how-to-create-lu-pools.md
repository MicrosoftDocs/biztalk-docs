---
title: "How to Create LU Pools1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_Pool_3270"
  - "SNA_Pool_Lua"
  - "SNA_Pool_Down"
ms.assetid: f548db93-cad4-4bf0-b12b-eef7c5b46894
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Create LU Pools
Although you can create individual LUs and assign them to users and groups, using LU pools to manage and deploy a large number of LUs is a more efficient method of administering these resources.  
  
 LU pools are groupings of 3270, LUA, or downstream LUs that allow you to maximize access to LUs. A user, LUA application, or downstream system using the pool can get LU access as long as one of the pooled LUs is available. If some of the pooled LUs are not functioning, the user, LUA application, or downstream system will not be affected, as long as another LU in the pool is available.  
  
 LU pools allow groups of intermittent users to use resources efficiently. For example, ten 3270 users who only need intermittent access may find that a pool of five 3270 LUs is adequate for their needs.  
  
 If a user needs access to multiple LU sessions, you can assign one LU or LU pool for each session that the user needs. A pool can be assigned multiple times to the same user.  
  
 An LU can be removed from an LU pool by simply deleting it from the pool.  
  
 The following procedures will help you manage your LU pools:  
  
-   To create LU pools  
  
-   To assign a 3270 LU to a connection  
  
-   To assign LUs and LU pools to users and groups  
  
-   To view LUs or pools assigned to users  
  
-   To add 3270 LUs to a pool  
  
-   To add a workstation and assign LUs  
  
-   To remove an LU from a pool  
  
### To create LU pools  
  
1.  In SNA Manager, right-click the **Pools** folder, point to **New**, and then click **3270 Display LU Pool**.  
  
2.  In **Pool Properties**, enter a name for your pool, up to eight characters in length. A comment is optional.  
  
3.  Leave the check box cleared, and click **OK**.  
  
4.  The new pool appears in the **Pools** folder.  
  
### To assign a 3270 LU to a connection  
  
1.  In SNA Manager, expand SNA service for the server you are working with, and then expand **Connections**.  
  
2.  Right-click the connection where you want to add the LU, point to **New**, and click the type of 3270 LU you want to assign.  
  
3.  In the **3270 LU Properties** box, enter the LU Name. The LU number is system-assigned.  
  
4.  Click **OK** to exit.  
  
5.  On the **Action** menu, click **Save Configuration**.  
  
### To assign LUs and LU pools to users and groups  
  
1.  In SNA Manager, right-click the LU or LU pool, click **Assign to User**, and then select the users you want to assign.  
  
2.  Click **OK**.  
  
3.  Verify that the state of the server is active and that the connections are available (either **OnDemand** or **Active**). If the server is not active, right-click the server in SNA Manager, and then click **Start**.  
  
### To view LUs or pools assigned to users  
  
1.  In SNA Manager, double-click **Configured Users**. Then click the user or group that you want to view. The details pane shows the LUs and pools assigned to that user or group, plus other details, such as status and LU number.  
  
2.  To view local or remote APPC LUs assigned to a user or group, right-click the targeted user or group, and click **Properties** under **Configured Users**. Click the **APPC Defaults** tab. When you are done viewing, click **Cancel**.  
  
### To add 3270 LUs to a pool  
  
1.  In SNA Manager, expand **Servers**, and then expand the server you are working with.  
  
2.  Expand **Connections**, and then click the connection that contains the needed 3270 LUs.  
  
3.  In the right pane, right-click the 3270 LU that you want to assign and click **Assign Pool**.  
  
4.  In the dialog box, click the pool to which you want to assign the LU, and then click **OK**.  
  
5.  Repeat steps 2 and 3 for each LU that you want to assign to a pool.  
  
6.  On the **Action** menu, click **Save Configuration**.  
  
> [!NOTE]
>  To verify that the LUs are in the correct pool, make sure the **Pools** node is expanded, double-click the name of the affected pool, and view its LUs in the details pane.  
  
> [!NOTE]
>  Both the LUs and the LU pool must be of the same type (3270).  
  
#### To add a workstation and assign LUs  
  
1.  In SNA Manager, right-click **Workstations**, point to **New**, and then click **Workstation**.  
  
2.  Fill in the **Workstation Properties** dialog box.  
  
3.  Click **OK** to add the new workstation.  
  
4.  To assign LUs to the workstation, double-click **Connections**, and then double-click the connection that contains the needed LUs.  
  
5.  Right-click the LU that you want to assign, and click **Assign to Workstation**.  
  
6.  In the dialog box, click the workstation, and then click **OK**.  
  
7.  On the **Action** menu, click **Save Configuration**.  
  
> [!NOTE]
>  All workstation users must be members of the same SNA subdomain. You can avoid having to add each user to the subdomain by assigning the **Everyone** group to the subdomain and assigning no LUs to the group.  
  
#### To remove an LU from a pool  
  
1.  In SNA Manager, click **Pools**.  
  
2.  Right-click the LU that you want to remove, and then click **Delete**.  
  
3.  In the **Confirmation** dialog box, click **Yes** to delete the LU.  
  
4.  On the **Action** menu, click **Save Configuration**.  
  
5.  On the **Action** menu, click **Refresh**.  
  
> [!NOTE]
>  An empty pool provides no LU access.  
  
## See Also  
 [Creating and Configuring LUs](../core/creating-and-configuring-lus.md)