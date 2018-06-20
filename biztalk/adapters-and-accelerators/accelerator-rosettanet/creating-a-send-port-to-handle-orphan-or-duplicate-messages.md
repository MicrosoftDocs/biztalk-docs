---
title: "Creating a Send Port to Handle Orphan or Duplicate Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, duplicate messages"
  - "messages, orphaned messages"
  - "send ports, duplicate messages"
  - "send ports, orphaned messages"
  - "messages, send ports"
ms.assetid: 61d51206-13e3-4d32-a184-866248db9b45
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating a Send Port to Handle Orphan or Duplicate Messages
This topic describes how to set up a send port that you can use to delete orphan or duplicate messages.  
  
 Orphan or duplicate messages can be a problem if [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] receives additional copies of a message after the public-process orchestration has completed processing the first copy of the message. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] marks those messages as duplicates and suspends them. You can view these messages in the BizTalk Administration Console. For more information about BizTalk Administration Console, see "Using the BizTalk Administration Console" in the BizTalk Server Help.  
  
 Orphan or duplicate messages remain in the BizTalk Administration Console until you review or delete them. The most effective way of deleting them is to set up a send port with filters set for orphan or duplicate messages. You can move them using any transportation means available in BizTalk Server. For example, you can move them by using File transport. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] sends the orphan or duplicate messages as files to a location on a hard disk. This lets you to delete them easily. The port can be in the enlisted and stopped state, in which case all messages sent to it will show as suspended under that send port.  
  
> [!NOTE]
>  Instead of creating a send port to handle duplicate/orphan messages, you can create a special pipeline component to delete these messages from the MessageBox database. You can use the FixMsg component in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SDK as a template. You have to modify the `IComponent.Execute` method to return null. This causes [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to discard any message sent to a pipeline that contains the component. You have to compile this pipeline component and add it to a send pipeline, and then compile, deploy, and select the send pipeline for the sink port. For more information, see "CustomComponent ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Sample)" in BizTalk Server Help.  
  
### To create a send port to handle orphan or duplicate messages  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **View** menu, click **BizTalk Explorer**.  
  
2. In BizTalk Explorer, expand **BizTalk Management Database**, and then expand **Send Ports**.  
  
3. Right-click **Send Ports**, and then click **Add Send Port**.  
  
4. In the Create New Send Port window, select **Static One-Way Port**, and then click **OK**.  
  
5. In the Static One-Way Send Port Properties window, in the **Name** box, type a name for the send port.  
  
6. In the left pane, click **Transport**. In the right pane, click **Transport Type**, and select **FILE** for the transport type. Click the ellipsis button (...) next to **Address (URI)**, type a location on your hard disk, and then click **OK**.  
  
7. In the left pane, click **Send**, click **Send Pipeline**, and then select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.  
  
8. In the left pane, click **Filters and Maps**, and then click **Filters**.  
  
9. On the first line in the right pane, for **Property**, select **Microsoft.Solutions.BTARN.GlobalSchemas.IsDuplicateMessage** from the drop-down list, leave the **Operator** as **==**, enter **True** for **Value**, and then select **Or** from the drop-down list for **Group**.  
  
10. On the second line in the right pane, for **Property**, select **Microsoft.Solutions.BTARN.GlobalSchemas.IsOrphanMessage** from the drop-down list, leave the **Operator** as **==**, and then enter **True** for **Value**.  
  
11. Click **OK**.  
  
12. In BizTalk Explorer, right-click the name of the send port, click **Enlist**. After the send port has been enlisted, right-click the send port, and then click **Start**.  
  
## See Also  
 [Programming Guide](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)