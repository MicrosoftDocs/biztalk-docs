---
title: "How to Change the Default Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications, default"
  - "applications, modifying"
  - "modifying, applications"
ms.assetid: cfa5e88f-0bbb-4edd-a840-722dcdcce266
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Change the Default Application
This topic describes how to change the default application by editing the properties of an application in the BizTalk Server Administration console. You can also change the default application by creating a new application and specifying it as the default application, as described in [How to Create an Application](../core/how-to-create-an-application.md).  
  
 When you install BizTalk Server, a default application named BizTalk Application 1 is created in the BizTalk Management database and appears in the BizTalk Server Administration console. When you upgrade from an earlier version of BizTalk Server, your artifacts are automatically placed in this application. In addition, when you import a Windows Installer (.msi) file by using BTSTask without specifying an application, the artifacts in the .msi file are imported into the default application.  
  
 You cannot delete the default application; however, you can change which application is the default. If you change the default application, you can then delete the application that was previously the default, if you want. For instructions, see [How to Delete a BizTalk Application from the BizTalk Group](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).  
  
 When you change the default application, all of the artifacts remain in the application that was originally the default. You can explicitly move the artifacts out of the application, if you want. For instructions, see [How to Move an Artifact to a Different Application](../core/how-to-move-an-artifact-to-a-different-application.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To change the default application  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, right-click the application that you want to make the default, and then click **Properties**.  
  
3. Select the **Make this the default application** check box, and click **OK**.  
  
## See Also  
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)