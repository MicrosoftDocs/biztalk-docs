---
title: "How to Refresh a Resource | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [resources], refreshing"
  - "refreshing resources"
  - "resources, refreshing"
ms.assetid: d6ff7c9d-8aaf-42a4-b1a3-00c05f6ac869
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Refresh a Resource
This topic describes how to use the BizTalk Server Administration console to refresh a resource artifact. This updates the artifact information in the BizTalk Management database. Another way to do this is by adding the artifact to the application using the BTSTask [AddResource Command](../core/addresource-command.md) with the overwrite option.  
  
 Resource artifacts are contained in an application's Resources folder. You might want to refresh a resource artifact if you make changes to the source file and want to replace the file in the application with the updated file.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To refresh a resource artifact  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the resource artifact to refresh, and then expand the application containing the artifact.  
  
3. Click the **Resources** folder, right-click the file to refresh, and then click **Modify**.  
  
4. In the **Modify Resources** dialog box, select the file to refresh, and then click **Refresh**.  
  
5. Browse to the updated file with which you want to replace the current file, and then click **OK**.  
  
    The current file is replaced with the updated file. In addition, the configuration, settings displayed on the **Options** tab of the **Modify Resources** dialog box are applied to the refreshed file. For more information about changing these settings, click **Help** in the dialog box.  
  
## See Also  
 [Managing Pre- and Post-processing Scripts](../core/managing-pre-and-post-processing-scripts.md)   
 [Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [Managing Resources](../core/managing-resources.md)