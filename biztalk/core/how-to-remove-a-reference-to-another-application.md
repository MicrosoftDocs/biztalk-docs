---
title: "How to Remove a Reference to Another Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications, references"
ms.assetid: cc867706-7c56-4386-b7ec-9fd7cf6c83a4
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove a Reference to Another Application
This topic describes how to use the BizTalk Server Administration console to remove a reference from one application to another application. You remove a reference when you no longer need to use an artifact in the current application that exists in another application in the same BizTalk group. For more information on adding references, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).  
  
 If artifacts in the current application still use artifacts in the referenced application, the operation to remove the reference will fail.  
  
> [!CAUTION]
>  Every application in BizTalk Server automatically contains a reference to the BizTalk.System application. This is because the artifacts that BizTalk.System contains are used by every BizTalk application. You should never remove a reference to the BizTalk.System application. If you do, your application may not function correctly.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To remove a reference to another application  
  
1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand  **BizTalk Server Administration**, right-click the application from which you want to remove a reference (the one that refers to another application), and then click **Properties**.  
  
3. In the left pane of the properties page, click **References**.  
  
4. In the right pane, click the application that you no longer want to reference from this application, click **Remove**, and then click **OK**.  
  
## See Also  
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)