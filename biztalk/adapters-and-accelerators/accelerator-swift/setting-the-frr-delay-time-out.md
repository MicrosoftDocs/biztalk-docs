---
description: "Learn more about: Setting the FRR Delay Time-Out"
title: "Setting the FRR Delay Time-Out"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Setting the FRR Delay Time-Out
You must configure the FRR orchestration to time out after some duration, so it will not wait for the FNN response indefinitely. If the time-out duration expires, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] publishes the timed-out messages to a custom time-out handler.  
  
### To set the FRR delay time-out  
  
1.  Click **Start**, click **Run**, type **regedit**, and then click **OK**.  
  
2.  In the left pane of the Registry Editor, move to My Computer/HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/BizTalk Accelerator for SWIFT/FRR.  
  
    > [!IMPORTANT]
    >  The role will be added in the position in the workflow that is defined in the Roles node. To change that position, you need to perform step 8 to change the order of the roles in the Roles node.  
  
3.  In the right pane of the Registry Editor, double-click **DelayTimeout**.  
  
4.  In the **Edit DWORD Value** dialog box, in the **Value data** box, type the time-out duration in hexadecimal format.  
  
    > [!NOTE]
    >  The default value for the **FRR DelayTimeout** property is 600 seconds (258 Hexadecimal).  
  
5.  Click **OK**.
