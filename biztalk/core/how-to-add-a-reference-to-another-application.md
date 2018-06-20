---
title: "How to Add a Reference to Another Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications, referencing"
ms.assetid: 6a177560-ee1f-403a-a68a-ade409a39a35
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a Reference to Another Application
This topic describes how to use the BizTalk Server Administration console to add a reference from one application to another application. You can also add a reference to the other application when you import your application by using the Import Wizard, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).  
  
 You add a reference when you want to use an artifact in the current application that already exists in another application in the same BizTalk group. This is because most types of artifacts must be unique in a BizTalk group. Rather than adding the duplicate artifact to the current application, you add a reference to the other application that already contains the artifact. For more information, see [Artifacts That Must Be Unique in an Application or Group](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).  
  
 It is not necessary to add a reference when you want to use a virtual directory or a certificate that already exists in another application. Furthermore, we recommend against doing this because it can create a circular reference.  
  
 When you import an application that has dependencies, references can be imported as well. When adding a reference to another application, bear in mind that this affects the way you deploy both applications. For more information, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To add a reference to another application  
  
1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and right-click the application in which you want to create a reference. This is the application in which you want to use an artifact that is contained in another application.  
  
3. Point to **Add** and then click **References**.  
  
4. In **Applications**, select the check box of the application to which you want to add a reference (the application containing the artifact or artifacts that you want to use), and then click **OK**.  
  
    The reference is added to the current application. In the console tree, a hand icon is added to the application that you referred from this application to indicate that it is referenced by one or more other applications.  
  
    ![Shared application icon](../core/media/sharedapplicationicon.gif "SharedApplicationIcon")  
  
## See Also  
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)