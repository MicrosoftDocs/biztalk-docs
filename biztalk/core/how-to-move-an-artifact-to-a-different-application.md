---
title: "How to Move an Artifact to a Different Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "artifacts, moving"
  - "applications, artifacts"
ms.assetid: 861e7782-0566-4478-a0bd-f8ced1ea6d56
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Move an Artifact to a Different Application
This topic describes how to move an artifact from one application to another within a BizTalk group by using the Move To Application command of the BizTalk Server Administration console. You might want to do this if you need to use an artifact that already exists in one application in a different application in the same BizTalk group.  
  
 When moving an artifact, bear in mind the following important points:  
  
-   **The applications must be in the same group.** The Move To Application command only works if the application from which you want to move the artifact is in the same BizTalk group as the application to which you want to move the artifact. If you want to move the artifact to an application in a different group, you can either export the artifact from the application in which it currently exists and then import it into the new application, or add the artifact to the application. For instructions, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md), [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md), and [How to Create or Add an Artifact](../core/how-to-create-or-add-an-artifact.md). You must then manually remove the artifact from the original application, as described in [How to Remove an Artifact from an Application](../core/how-to-remove-an-artifact-from-an-application.md).  
  
-   **Moving an artifact may also move artifacts on which it depends or that depend on it.** When you move an artifact to a new application, any other artifacts on which it has dependencies are also moved unless the new application has a reference to the application(s) containing the artifacts on which the moved artifact depends. Also, any artifacts that have dependencies on the moved artifact are moved unless the application(s) containing them have a reference to the new application. When moving an artifact, you are shown the list of other artifacts that will also be moved.  
  
> [!NOTE]
>  If you need to use the same artifact in two or more applications, you may need to create a reference from the application in which you want to use the artifact to the one currently containing the artifact. This is because certain types of artifacts must be unique in a BizTalk group. For more information, see [Artifacts That Must Be Unique in an Application or Group](../core/artifacts-that-must-be-unique-in-an-application-or-group.md). For instructions on adding references, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md). Be aware that adding a reference to another application creates dependencies between the applications and affects the way you must deploy them. For background information, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To move an artifact to a different application  
  
1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then expand the application from which you want to move an artifact.  
  
3. Click the folder containing the artifact that you want to move, right-click the artifact, and then click **Move To Application**.  
  
4. In the **Destination application** box, click the arrow, and then click the application to which you want to move the artifact.  
  
    The **Moving Artifacts** box displays the artifact to move, along with all dependent artifacts, which will be moved as well.  
  
5. Click **OK**.  
  
## See Also  
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)