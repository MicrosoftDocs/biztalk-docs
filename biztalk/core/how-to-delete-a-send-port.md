---
title: "How to Delete a Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [send ports], deleting"
  - "send ports, deleting"
  - "deleting, send ports"
ms.assetid: aff5980e-57bf-400c-82bd-3d02e143f227
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Delete a Send Port
This topic describes how to use the BizTalk Server Administration console to delete a send port from a BizTalk application. When you do this, the send port is also deleted from the BizTalk Management database for the group.  
  
> [!IMPORTANT]
>  When you delete a send port, any running service instances associated with that port can no longer obtain configuration information about the send port, such as its name. Although this information is cached, if the service instance must resend a message, it will not be able to complete, and the message will be suspended. Before deleting a send port, you should verify that there are no running service instances, as described in [How to View Instance Information for a Send Port](../core/how-to-view-instance-information-for-a-send-port.md).  
  
 You can delete a send port only if it meets the following conditions:  
  
-   An orchestration is not bound to the send port. If this is the case, you can remove the binding by following the instructions in [How to Unbind an Orchestration](../core/how-to-unbind-an-orchestration.md).  
  
-   The send port is both stopped and unenlisted. For instructions on stopping and unenlisting a send port, see [How to Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md) and [How to Stop a Send Port or Send Port Group](../core/how-to-stop-a-send-port-or-send-port-group.md).  
  
-   The send port is not referenced by a party. For instructions on removing a reference to a send port from a party, see [How to View or Edit a Party](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca).  
  
-   The send port is not included in a send port group. For instructions on removing a send port from a send port group, see [How to Remove a Send Port from a Send Port Group](../core/how-to-remove-a-send-port-from-a-send-port-group.md).  
  
> [!NOTE]
>  The application developer can delete a send port during the development process by using the procedure in this topic.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To delete a send port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand BizTalk Server Administration, expand the BizTalk group, expand Applications, and then expand the application containing the send port that you want to delete  
  
3. Click **Send Ports**, right-click the send port, and then click **Delete**.  
  
## See Also  
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)