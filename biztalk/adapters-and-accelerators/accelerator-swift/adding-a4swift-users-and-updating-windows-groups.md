---
title: "Adding A4SWIFT Users and Updating Windows Groups | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "user accounts, Windows groups"
  - "Windows groups, user accounts"
  - "user accounts, creating"
  - "Windows groups, updating"
  - "updating Windows groups"
  - "A4SWIFT, creating user accounts"
ms.assetid: ddc54457-6499-402c-9cc2-f7b17bbc255f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adding A4SWIFT Users and Updating Windows Groups
After you create and install certificates for Message Repair and New Submission roles, you must create [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] users and add [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] users to groups.  
  
 **Summary**  
  
 Create Message Repair and New Submission users and add local or domain accounts to [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] user groups, as follows:  
  
- In the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Management Console, you need to create as many users as there are roles in the workflow stages of your Message Repair and New Submission process. Associate a distinct certificate with each of these users.  
  
- Using the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Computer Management utility, add each local user who is creating, repairing, verifying, or approving a message to the A4SWIFT Users.  
  
- Using the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Computer Management utility, add the local user that is listed in the Log On As field for the BizTalk Service BizTalk Group service to the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Users group.  
  
  > [!NOTE]
  >  For more information about [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] users and roles, see [Creating Departments and Roles for Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md).  
  
### To add User Accounts to the A4SWIFT Users Group  
  
1.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Computer Management**.  
  
2.  In the **Computer Management** dialog box, in the left pane, expand **Local Users and Groups**, and then click **Groups**.  
  
3.  In the **Computer Management** dialog box, in the right pane, double-click **A4SWIFT Users**.  
  
4.  In the **A4SWIFT Users Properties** dialog box, click **Add**.  
  
5.  In the **Select Users, Computers, or Groups** dialog box, in the **Enter the object names to select** pane, type the name of a local user who is creating, repairing, verifying, or approving a message, and then click **OK**.  
  
6.  Repeat step 5 for each local user who is creating, repairing, verifying, or approving a message.  
  
7.  In the A4SWIFT Users Properties dialog box, click **OK**.  
  
8.  In the Computer Management dialog box, in the left pane, expand Services and Applications, and then click Services. In the right pane, click **BizTalk Service BizTalk Group**. Note the user listed in the Log On As column for **BizTalk Service BizTalk Group**.  
  
9. In the left pane of the **Computer Management** dialog box, expand **Local Users and Groups**, and then click **Groups**. Double-click **A4SWIFT Users**. Ensure that the user listed in the Log On As column for **BizTalk Service BizTalk Group** is part of the **A4SWIFT Users** group. If not, add that user to the **A4SWIFT Users** group.  
  
10. Log off the server, and then log back on.